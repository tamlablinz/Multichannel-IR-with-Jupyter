# IR-multichannel
Calculate multichannel IR files through deconvolution of a recorded sine sweep, by Enrique Tomás and Ben Wesch at Tangible Music Lab Linz. 

Examples and Jupyter notebook included to illustrate the process.
To open the notebook, you need to have Jupyter installed (see https://jupyter.org/install). Some python libraries are also needed: numpy, scipy, wavio, matplot and warnings. Install them with pip or conda if you get the typical "module not found error". 

## Instructions for Jupyter notebook
* Download or clone this repository to a new folder on your computer. 
* Run Jupyter from a terminal in this folder via `jupyter notebook`.
* Open the Jupyter notebook `IR-Qq-multichannel.ipynb` and execute the cells from top to bottom. 

## Instructions for command line
You can also simply run the `deconvolve.py` file from your command line (after `chmod +x deconvolve.py`).

The help will guide you through the parameters and optional settings:
`./deconvolve.py -h`
```
usage: deconvolve.py [-h] [--limit {normalize,clip}] [--crop <threshold>] [--bitdepth <bitdepth>]
                     [--amp <amplification>]
                     sweepfile recfile outfile

positional arguments:
  sweepfile             filename of original sweep
  recfile               filename of recorded sweep (mono or multichannel)
  outfile               filename for extracted impulse response (channels identical to recfile)

options:
  -h, --help            show this help message and exit
  --limit {normalize,clip}
                        Normalize or clip resulting amplitudes
  --crop <threshold>    Crop resulting samples below threshold at start and end
  --bitdepth <bitdepth>
                        Set bit depth for outfile (defaults to 24)
  --amp <amplification>
                        Amplify resulting impulse response by given dB value
```

## Creating your own IRs
A mono sweep is included in the repository. Record the sweep in a room with a microphone (mono, stereo or arbitrary number of channels) and follow instructions in notebook.

This code generates IR files with the same number of channels as the recorded sweep you are using.

You can use the resulting .wav file with plugins like MatrixConv (https://leomccormack.github.io/sparta-site/docs/plugins/sparta-suite/#matrixconv) in combination with HO-SIRR (https://leomccormack.github.io/sparta-site/docs/plugins/hosirr/) for adding an ambisonics room to your track in real time. 
