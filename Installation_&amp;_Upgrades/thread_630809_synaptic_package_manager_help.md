---
title: "synaptic package manager help"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by eschmidt90 on 2007-12-03
I'm not sure if this is the right place to post, if it isn't, I apologize.

I've been trying to install some libraries on my PPC G4 machine running ubuntu edgy eft, but errors keep popping up.  Actually the errors pop up no matter what I try to install.  The error is as posted:

E: emacs21: subprocess post-installation script returned error exit status 1
E: cedet-common: dependency problems - leaving unconfigured
E: eieio: dependency problems - leaving unconfigured
E: graphviz-cairo: subprocess post-installation script returned error exit status 127
E: speedbar: dependency problems - leaving unconfigured

Any ideas why this is happening?  I've tried searching for and installing the listed packages, but that doesn't even help!  I've been trying to install the libraries using the Synaptic Package Manager.

TIA

-Erik Schmidt

---

### Post by zvacet on 2007-12-04
You will find all packages [here](http://packages.ubuntu.com/). Be sure to install all dependencies(marked with red ball)first.Before you download them you can chek with synaptic(type name in search box) if you allready have them(dependencies).Of course you will download just missing ones.After that install package.

---

### Post by eschmidt90 on 2007-12-04
Might not have been clear, my bad.  These same errors, possibly worded a little differently, come up when I try searching for and installing dependencies.

---

### Post by eschmidt90 on 2007-12-04
alright, I uninstalled emacs completely and most of the errrors go away, now I just get an error for graphiz-cairo post installation script

---

