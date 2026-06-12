---
title: "dpkg dpendency problems"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by recif on 2008-08-04
Hi,
 I was having some problems with my latex installation on an AMD64 mahine running Ubuntu 8.04, so I tried uninstalling and reinstalling tetex (which seems to require texlive) using: 
sudo apt-get install tetex-bin
but I get dependency errors (listed below).
I tried sudo spt-get install -f and sudo dpkg --configure -a
but the get the same errors.

I would appreciate some help in fixing this problem.
Recif
 

Setting up texlive-base-bin (2007.dfsg.1-2) ...
Running mktexlsr. This may take some time... done.
Building format(s) --all.
	This may take some time... 
fmtutil-sys failed. Output has been stored in
/tmp/fmtutil.ulG19600
Please include this file if you report a bug.

dpkg: error processing texlive-base-bin (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-base:
 texlive-base depends on texlive-base-bin (>= 2007-13); however:
  Package texlive-base-bin is not configured yet.
dpkg: error processing texlive-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-recommended:
 texlive-fonts-recommended depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-fonts-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured

---

### Post by tamoneya on 2008-08-04
it seems to be less related to dpgk/apt-get and more to do with the installer crashing.  can we take a look at /tmp/fmtutil.ulG19600

---

### Post by recif on 2008-08-05
Hi,
It seems that the problem was with the installation of the kpathsea library. I reinstalled it and then texlive, and that fixed the problem. Thanks for your assistance.
Recif

---

