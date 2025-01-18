# MW-sourcefind

## Purpose

This is the standalone LoTSS sourcefind code, broken out of the
ddf-pipeline repository for ease of use in the MW project and to allow profiling.

## Description

The repo contains a recipe for a singularity image for PyBDSF, the main dependency, plus the `sourcefind.py` wrapper used by LoTSS.

## JIRA links

https://jira.skatelescope.org/browse/TEAL-795

## Main developer

Martin Hardcastle (and ddf-pipeline collaborators)

## Files (components)

* sourcefind.py -- PyBDSF wrapper script. Taken from the DDF-pipeline source finder.
* pybdsf.singularity -- Singularity recipe. Use this to build the singularity image, then run `sourcefind.py` inside it.

## Inputs and outputs

Input: either one or two FITS image files suitable for feeding to PyBDSF.

Output: a FITS source catalogue and some ancillary products of the form used by LoTSS.

## Example of use

```
singularity build pybdsf.sif pybdsf.singularity
singularity shell pybdsf.sif
sourcefind.py --intfile my_fits_image.fits
```

## Software requirements

* If singularity image used, only singularity is needed
* If standalone, requirements are documented in the singularity, principal ones being PyBDSF, astropy and photutils.

## Hardware requirements

* RAM on the node must be sufficient for PyBDSF to run and work with the image, i.e. at a minimum several times the image size.
* PyBDSF will make use of multiple cores, though with decreasing efficiency.


