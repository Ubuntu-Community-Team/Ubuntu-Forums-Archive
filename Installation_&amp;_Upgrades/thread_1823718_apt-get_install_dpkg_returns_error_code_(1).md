---
title: "apt-get install: dpkg returns error code (1)"
date: 2011-08-12
forum: Installation &amp; Upgrades
---

### Post by mattrition on 2011-08-12
Currently, whenever I try sudo apt-get install or upgrade I get the following error:

```

tgac@tgac-VirtualBox:~/Dropbox/diss/data/shorebird$ sudo apt-get install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
15 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up tex-common (2.08) ...
Running mktexlsr. This may take some time... done.
texlive-base is not ready, delaying updmap-sys call
texlive-base is not ready, skipping fmtutil-sys --all call
Setting up texlive-base (2009-10) ...
Running mktexlsr. This may take some time... done.
Building format(s) --all --cnffile /etc/texmf/fmt.d/10texlive-base.cnf.
	This may take some time... 
fmtutil-sys failed. Output has been stored in
/tmp/fmtutil.o8yMVkfL
Please include this file if you report a bug.

dpkg: error processing texlive-base (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on texlive-latex-base (>= 2009-1); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-xcolor:
 latex-xcolor depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing latex-xcolor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pgf:
 pgf depends on latex-xcolor (>= 2.00-1); however:
  Package latex-xcoNo apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                                               No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                              No apport report written because MaxReports has already been reached
                                                                                                                                                  No apport report written because MaxReports has already been reached
                                                         No apport report written because MaxReports has already been reached
                                                                                                                             No apport report written because MaxReports has already been reached
                                    No apport report written because MaxReports has already been reached
                                                                                                        No apport report written because MaxReports has already been reached
               No apport report written because MaxReports has already been reached
                                                                                   No apport report written because MaxReports has already been reached
                                                                                                                                                       No apport report written because MaxReports has already been reached
                                                              No apport report written because MaxReports has already been reached
                                                                                                                                  No apport report written because MaxReports has already been reached
                                         lor is not configured yet.
 pgf depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing pgf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-beamer:
 latex-beamer depends on pgf (>= 1.00-1); however:
  Package pgf is not configured yet.
 latex-beamer depends on latex-xcolor (>= 2.00-1); however:
  Package latex-xcolor is not configured yet.
 latex-beamer depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing latex-beamer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-generic-recommended:
 texlive-generic-recommended depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-generic-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pstricks:
 texlive-pstricks depends on texlive-generic-recommended (>= 2009-1); however:
  Package texlive-generic-recommended is not configured yet.
 texlive-pstricks depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-pstricks (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of prosper:
 prosper depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 prosper depends on texlive-pstricks; however:
  Package texlive-pstricks is not configured yet.
 prosper depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing prosper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-extra-utils:
 texlive-extra-utils depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-extra-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-font-utils:
 texlive-font-utils depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-font-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-recommended:
 texlive-fonts-recommended depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-fonts-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-luatex:
 texlive-luatex depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-luatex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tipa:
 tipa depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing tipa (--configure):
 dependency problems - leaving unconfigured
Processing triggers for tex-common ...
texlive-base is not ready, delaying updmap-sys call
Building e-tex based formats --byhyphen /var/lib/texmf/tex/generic/config/language.def.
	This may take some time... 
fmtutil-sys failed. Output has been stored in
/tmp/fmtutil.jT9N2r44
Please include this file if you report a bug.

dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 texlive-base
 texlive-latex-base
 texlive-latex-recommended
 latex-xcolor
 pgf
 latex-beamer
 texlive-generic-recommended
 texlive-pstricks
 prosper
 texlive-extra-utils
 texlive-font-utils
 texlive-fonts-recommended
 texlive-luatex
 tipa
 tex-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

It's preventing me from installing alot of things, including upgrading r-base, and as you can probably tell my tex-live package is not usable. I had a little google and I found people with similar problems but not quite the same.

---

### Post by raja.genupula on 2011-08-12
man i too had faced the problem , i had posted a thread too on this . the thing i know for solving this is simply waiting for some time and then give a try or restart the system and try to install again .

---

### Post by mattrition on 2011-08-13
Well, at least I'm not the only one! This has been a problem on my distribution for a while now though. I first noticed it when I tried installing tex-live, but I couldn't say whether it was that attempt that caused it or if the problem was there before hand.

---

### Post by smrahmani on 2011-11-05
Is the problem solved?
I have it too. It's very urgent.

---

