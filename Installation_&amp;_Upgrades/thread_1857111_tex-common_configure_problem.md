---
title: "tex-common configure problem"
date: 2011-10-09
forum: Installation &amp; Upgrades
---

### Post by aqshin on 2011-10-09
It has been awhile that I am having problem with configuring tex-common package. This is the result of "sudo dpkg --configure -a":

```

Setting up tex-common (2.06ubuntu0.1) ...
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... 
updmap-sys failed. Output has been stored in
/tmp/updmap.UqQ7iwSg
Please include this file if you report a bug.

Sometimes, not accepting conffile updates in /etc/texmf/updmap.d
causes updmap-sys to fail.  Please check for files with extension
.dpkg-dist or .ucf-dist in this directory

dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of prosper:
 prosper depends on tex-common (>= 1.10); however:
  Package tex-common is not configured yet.
dpkg: error processing prosper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-generic-recommended:
 texlive-generic-recommended depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-generic-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pictures:
 texlive-pictures depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-pictures (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of asymptote:
 asymptote depends on tex-common (>= 1.18); however:
  Package tex-common is not configured yet.
dpkg: error processing asymptote (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pstricks:
 texlive-pstricks depends on texlive-generic-recommended (>= 2009-1); however:
  Package texlive-generic-recommended is not configured yet.
 texlive-pstricks depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-pstricks (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-beamer:
 latex-beamer depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing latex-beamer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-font-utils:
 texlive-font-utils depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-font-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-common:
 texlive-common depends on tex-common (>= 2.0); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-extra:
 texlive-latex-extra depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-latex-extra depends on texlive-common (>= 2009-1); however:
  Package texlive-common is not configured yet.
 texlive-latex-extra depends on texlive-pictures (>= 2009-1); however:
  Package texlive-pictures is not configured yet.
 texlive-latex-extra depends on texlive-latex-base (>= 2009-1); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-latex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-extra-utils:
 texlive-extra-utils depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-extra-utils depends on texlive-common (>= 2009-1); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-extra-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-xcolor:
 latex-xcolor depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing latex-xcolor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pgf:
 pgf depends on latex-xcolor (>= 2.00-1); however:
  Package latex-xcolor is not configured yet.
 pgf depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing pgf (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tex-common
 prosper
 texlive-generic-recommended
 texlive-pictures
 asymptote
 texlive-latex-recommended
 texlive-pstricks
 texlive-latex-base
 latex-beamer
 texlive-font-utils
 texlive-common
 texlive-latex-extra
 texlive-extra-utils
 latex-xcolor
 pgf

```

If I grep lines with "depends" words:
```

 prosper depends on tex-common (>= 1.10); however:
 texlive-generic-recommended depends on tex-common (>= 2.00); however:
 texlive-pictures depends on tex-common (>= 2.00); however:
 asymptote depends on tex-common (>= 1.18); however:
 texlive-latex-recommended depends on tex-common (>= 2.00); however:
 texlive-pstricks depends on texlive-generic-recommended (>= 2009-1); however:
 texlive-pstricks depends on tex-common (>= 2.00); however:
 texlive-latex-base depends on tex-common (>= 2.00); however:
 latex-beamer depends on texlive-latex-base; however:
 texlive-font-utils depends on tex-common (>= 2.00); however:
 texlive-common depends on tex-common (>= 2.0); however:
 texlive-latex-extra depends on tex-common (>= 2.00); however:
 texlive-latex-extra depends on texlive-common (>= 2009-1); however:
 texlive-latex-extra depends on texlive-pictures (>= 2009-1); however:
 texlive-latex-extra depends on texlive-latex-base (>= 2009-1); however:
 texlive-extra-utils depends on tex-common (>= 2.00); however:
 texlive-extra-utils depends on texlive-common (>= 2009-1); however:
 latex-xcolor depends on texlive-latex-recommended; however:
 pgf depends on latex-xcolor (>= 2.00-1); however:
 pgf depends on texlive-latex-recommended; however:

```


I have read some posts and tried, but nothing worked for me. I think the problem is with tex-common configuration file and some line(s) should be changed, but I can't find such post.

Any help would be much appreciated.

---

### Post by aqshin on 2011-10-09
Sorry, I forgot to mention Ubuntu version I use. It's **10.04**.

---

