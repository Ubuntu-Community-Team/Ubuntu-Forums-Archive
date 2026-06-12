---
title: "latex won't install :("
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by scohop on 2008-04-12
I'm a long time Linux-er but new to Ubuntu.  I'm trying not to hate it with the fire of a thousand suns. :)

I'm trying to install LaTeX, as so:

sudo apt-get install texlive

Here's the error message,

> Setting up texlive-base-bin (2007-12ubuntu3.1) ...
Running mktexlsr. This may take some time... done.
Building format(s) --all.
        This may take some time...
fmtutil-sys failed. Output has been stored in
/tmp/fmtutil.wIabP781
Please include this file if you report a bug.

dpkg: error processing texlive-base-bin (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-base:
 texlive-base depends on texlive-base-bin (>= 2007-8); however:
  Package texlive-base-bin is not configured yet.
dpkg: error processing texlive-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-recommended:
 texlive-fonts-recommended depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-fonts-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2007-7); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on texlive-latex-base (>= 2007-7); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive:
 texlive depends on texlive-fonts-recommended (>= 2007-7); however:
  Package texlive-fonts-recommended is not configured yet.
 texlive depends on texlive-latex-recommended (>= 2007-7); however:
  Package texlive-latex-recommended is not configured yet.
 texlive depends on texlive-latex-base (>= 2007-7); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive (--configure):
 dependency problems - leaving unconfigured



And sudo cat /tmp/fmtutil.wIabP781 gives:

> tcfmgr: config file `tcfmgr.map' (usually in $TEXMFMAIN/texconfig) not found.
fmtutil: config file `fmtutil.cnf' not found.


Any help will be greatly appreciated!

pax,
Scott

---

### Post by scohop on 2008-04-12
Just an update, the blasted thing still won't work.

I've tried removing and reinstalling all the related packages.

No luck.

pax,
Scott

---

