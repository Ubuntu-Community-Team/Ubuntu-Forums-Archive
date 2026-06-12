---
title: "texlive can't find latex.fmt"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by ajohansen on 2008-02-23
I downloaded Ubuntu 7.10 yesterday and everything works great.

BUT I simply am unable to get latex to work. I downloaded the texlive package through Synapse (which gives a "decent selection" of texlive packages). Downloading and installing went smooth. However when I try to compile a latex file I get the error message:

  This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6) 
   %&-line parsing enabled.
  kpathsea: Running mktexfmt latex.fmt
  I can't find the format file `latex.fmt'!

I've looked everywhere on the hard disk for the latex.fmt file (of course also in /usr/share/texmf-texlive/web2c), but the file does not exist. I read in other threads about people who either set their TEXINPUTS env variable wrong or who could create the missing files by running texconfig, but I have checked that TEXINPUTS is set to /usr/share/texmf-texlive and 'texconfig init' does not create the missing latex.fmt file.

Since latex is the single most important program that needs to run on my laptop any help on how to solve this problem will be much appreciated.

---

### Post by ajohansen on 2008-02-23
I think I found the problem. I had set TEXINPUTS to a range of directories to look for latex files. Setting instead TEXINPUTS= caused texlive to install properly.

This may even be a bug in the texlive installation, since many users will probably have set TEXINPUTS (in .bashrc or .cshrc) before they install texlive.

---

