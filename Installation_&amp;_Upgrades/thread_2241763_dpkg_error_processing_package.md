---
title: "dpkg: error processing package"
date: 2014-08-28
forum: Installation &amp; Upgrades
---

### Post by gor4l on 2014-08-28
Hi again.
I can`t update ubuntu 14.04. and install packeges from sudo apt-get install

Can someone help?

Log from synaptic
```

(synaptic:30337): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
Selecting previously unselected package libcdt5.
(Reading database ... 410860 files and directories currently installed.)
Preparing to unpack .../libcdt5_2.36.0-0ubuntu3_amd64.deb ...
Unpacking libcdt5 (2.36.0-0ubuntu3) ...
Selecting previously unselected package libcgraph6.
Preparing to unpack .../libcgraph6_2.36.0-0ubuntu3_amd64.deb ...
Unpacking libcgraph6 (2.36.0-0ubuntu3) ...
Preparing to unpack .../graphviz_2.36.0-0ubuntu3_amd64.deb ...
Unpacking graphviz (2.36.0-0ubuntu3) over (2.26.3-10ubuntu1.1) ...
Processing triggers for man-db (2.6.7.1-1) ...
(Reading database ... 410881 files and directories currently installed.)
Removing libgvc5 (2.26.3-10ubuntu1.1) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.1) ...
Selecting previously unselected package libgvc6.
(Reading database ... 410862 files and directories currently installed.)
Preparing to unpack .../libgvc6_2.36.0-0ubuntu3_amd64.deb ...
Unpacking libgvc6 (2.36.0-0ubuntu3) ...
Selecting previously unselected package libgvpr2.
Preparing to unpack .../libgvpr2_2.36.0-0ubuntu3_amd64.deb ...
Unpacking libgvpr2 (2.36.0-0ubuntu3) ...
Selecting previously unselected package linux-image-3.13.0-34-generic.
Preparing to unpack .../linux-image-3.13.0-34-generic_3.13.0-34.60_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-34-generic (3.13.0-34.60) ...
Selecting previously unselected package linux-image-extra-3.13.0-34-generic.
Preparing to unpack .../linux-image-extra-3.13.0-34-generic_3.13.0-34.60_amd64.deb ...
Unpacking linux-image-extra-3.13.0-34-generic (3.13.0-34.60) ...
Preparing to unpack .../linux-generic_3.13.0.34.40_amd64.deb ...
Unpacking linux-generic (3.13.0.34.40) over (3.13.0.27.33) ...
Preparing to unpack .../linux-image-generic_3.13.0.34.40_amd64.deb ...
Unpacking linux-image-generic (3.13.0.34.40) over (3.13.0.27.33) ...
Selecting previously unselected package linux-headers-3.13.0-34.
Preparing to unpack .../linux-headers-3.13.0-34_3.13.0-34.60_all.deb ...
Unpacking linux-headers-3.13.0-34 (3.13.0-34.60) ...
Selecting previously unselected package linux-headers-3.13.0-34-generic.
Preparing to unpack .../linux-headers-3.13.0-34-generic_3.13.0-34.60_amd64.deb ...
Unpacking linux-headers-3.13.0-34-generic (3.13.0-34.60) ...
Preparing to unpack .../linux-headers-generic_3.13.0.34.40_amd64.deb ...
Unpacking linux-headers-generic (3.13.0.34.40) over (3.13.0.27.33) ...
Processing triggers for man-db (2.6.7.1-1) ...
Setting up tex-common (4.04) ...
Ignoring /etc/texmf/texmf.d/05TeXMF.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/15Plain.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/45TeXinputs.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/55Fonts.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/65BibTeX.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/75DviPS.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/80DVIPDFMx.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/85Misc.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/90TeXDoc.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/95NonPath.cnf during generation of texmf.cnf, please remove manually!
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... 
updmap-sys failed. Output has been stored in
/tmp/updmap.H8Xp3Wp5
Please include this file if you report a bug.

Sometimes, not accepting conffile updates in /etc/texmf/updmap.d
causes updmap-sys to fail.  Please check for files with extension
.dpkg-dist or .ucf-dist in this directory

dpkg: error processing package tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of latex-sanskrit:
 latex-sanskrit depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package latex-sanskrit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lmodern:
 lmodern depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package lmodern (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tex-gyre:
 tex-gyre depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package tex-gyre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-latex-base No apport report written because the error message indicates its a followup error from a previous failure.
                                                                     No apport report written because the error message indicates its a followup error from a previous failure.
 No apport report written because MaxReports is reached already
                                                               No apport report written because MaxReports is reached already
                                      No apport report written because MaxReports is reached already
             No apport report written because MaxReports is reached already
                                                                           No apport report written because MaxReports is reached already
                                                  No apport report written because MaxReports is reached already
                         No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                     No apport report written because MaxReports is reached already
            No apport report written because MaxReports is reached already
                                                                          (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-generic-recommended:
 texlive-generic-recommended depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-generic-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pstricks:
 texlive-pstricks depends on texlive-generic-recommended (>= 2013.20130512); however:
  Package texlive-generic-recommended is not configured yet.
 texlive-pstricks depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-pstricks (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of asymptote:
 asymptote depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 asymptote depends on texlive-pstricks; howevNo apport report written because MaxReports is reached already
                    No apport report written because MaxReports is reached already
                                                                                  No apport report written because MaxReports is reached already
                                                         No apport report written because MaxReports is reached already
                                No apport report written because MaxReports is reached already
       No apport report written because MaxReports is reached already
                                                                     No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                   No apport report written because MaxReports is reached already
                                                                                 No apport report written because MaxReports is reached already
                                                        No apport report written because MaxReports is reached already
                               No apport report written because MaxReports is reached already
      No apport report written because MaxReports is reached already
                                                                    er:
  Package texlive-pstricks is not configured yet.
 asymptote depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package asymptote (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.
 texlive-latex-recommended depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cm-super-minimal:
 cm-super-minimal depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.
 cm-super-minimal depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.

dpkg: error procNo apport report written because MaxReports is reached already
                                                                              No apport report written because MaxReports is reached already
                                                     No apport report written because MaxReports is reached already
                            No apport report written because MaxReports is reached already
   No apport report written because MaxReports is reached already
                                                                 No apport report written because MaxReports is reached already
                                        No apport report written because MaxReports is reached already
               No apport report written because MaxReports is reached already
                                                                             No apport report written because MaxReports is reached already
                                                    No apport report written because MaxReports is reached already
                           No apport report written because MaxReports is reached already
  No apport report written because MaxReports is reached already
                                                                No apport report written because MaxReports is reached already
                                       essing package cm-super-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cm-super:
 cm-super depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.
 cm-super depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
 cm-super depends on cm-super-minimal (= 0.3.4-9); however:
  Package cm-super-minimal is not configured yet.

dpkg: error processing package cm-super (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-metapost:
 texlive-metapost depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-metapost (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of context:
 context depends on texlive-metapost (>= 2013); however:
  Package texlive-metapost is not conNo apport report written because MaxReports is reached already
            No apport report written because MaxReports is reached already
                                                                          No apport report written because MaxReports is reached already
                                                 No apport report written because MaxReports is reached already
                        No apport report written because MaxReports is reached already
                                                                                      No apport report written because MaxReports is reached already
                                                             No apport report written because MaxReports is reached already
                                    No apport report written because MaxReports is reached already
           No apport report written because MaxReports is reached already
                                                                         No apport report written because MaxReports is reached already
                                                No apport report written because MaxReports is reached already
                       figured yet.
 context depends on lmodern (>= 2.004.4); however:
  Package lmodern is not configured yet.
 context depends on tex-gyre; however:
  Package tex-gyre is not configured yet.
 context depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.

dpkg: error processing package context (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of context-modules:
 context-modules depends on context (>> 2011); however:
  Package context is not configured yet.
 context-modules depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package context-modules (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-font-utils:
 texlive-font-utils depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-font-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-extra-utils:
 texlive-extra-utils depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.
 texlive-extra-utils depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package texlive-extra-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of feynmf:
 feynmf depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.
 feynmf depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 feynmf depends on texlive-font-utils; however:
  Package texlive-font-utils is not configured yet.
 feynmf depends on texlive-extra-utils; however:
  Package texlive-extra-utils is not configured yet.

dpkg: error processing package feynmf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-xcolor:
 latex-xcolor depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
 latex-xcolor depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package latex-xcolor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-beamer:
 latex-beamer depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.
 latex-beamer depends on latex-xcolor (>= 2.00-1); however:
  Package latex-xcolor is not configured yet.
 latex-beamer depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package latex-beamer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-cjk-common:
 latex-cjk-common depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 latex-cjk-common depends on texlive-font-utils (>= 2007.dfsg.2-1); however:
  Package texlive-font-utils is not configured yet.
 latex-cjk-common depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.

dpkg: error processing package latex-cjk-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-cjk-chinese:
 latex-cjk-chinese depends on latex-cjk-common (= 4.8.3+git20120914-2ubuntu1); however:
  Package latex-cjk-common is not configured yet.
 latex-cjk-chinese depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package latex-cjk-chinese (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-cjk-japanese:
 latex-cjk-japanese depends on latex-cjk-common (= 4.8.3+git20120914-2ubuntu1); however:
  Package latex-cjk-common is not configured yet.
 latex-cjk-japanese depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.

dpkg: error processing package latex-cjk-japanese (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-cjk-korean:
 latex-cjk-korean depends on latex-cjk-common (>= 4.8.3+git20120914-2ubuntu1); however:
  Package latex-cjk-common is not configured yet.
 latex-cjk-korean depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.

dpkg: error processing package latex-cjk-korean (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-other:
 texlive-lang-other depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-other (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-cjk-thai:
 latex-cjk-thai depends on latex-cjk-common (>= 4.8.3+git20120914-2ubuntu1); however:
  Package latex-cjk-common is not configured yet.
 latex-cjk-thai depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 latex-cjk-thai depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.
 latex-cjk-thai depends on texlive-lang-other (>= 2013.20130523-1); however:
  Package texlive-lang-other is not configured yet.

dpkg: error processing package latex-cjk-thai (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-cjk-all:
 latex-cjk-all depends on latex-cjk-common (>= 4.8.3+git20120914-2ubuntu1); however:
  Package latex-cjk-common is not configured yet.
 latex-cjk-all depends on latex-cjk-chinese (>= 4.8.3+git20120914-2ubuntu1); however:
  Package latex-cjk-chinese is not configured yet.
 latex-cjk-all depends on latex-cjk-japanese (>= 4.8.3+git20120914-2ubuntu1); however:
  Package latex-cjk-japanese is not configured yet.
 latex-cjk-all depends on latex-cjk-korean (= 4.8.3+git20120914-2ubuntu1); however:
  Package latex-cjk-korean is not configured yet.
 latex-cjk-all depends on latex-cjk-thai (= 4.8.3+git20120914-2ubuntu1); however:
  Package latex-cjk-thai is not configured yet.

dpkg: error processing package latex-cjk-all (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latexmk:
 latexmk depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package latexmk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of m-tx:
 m-tx depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.

dpkg: error processing package m-tx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of musixtex:
 musixtex depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.

dpkg: error processing package musixtex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pmx:
 pmx depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.
 pmx depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package pmx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of purifyeps:
 purifyeps depends on texlive-metapost; however:
  Package texlive-metapost is not configured yet.

dpkg: error processing package purifyeps (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rubber:
 rubber depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package rubber (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-recommended:
 texlive-fonts-recommended depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-fonts-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive:
 texlive depends on texlive-latex-recommended (>= 2013.20130512); however:
  Package texlive-latex-recommended is not configured yet.
 texlive depends on texlive-fonts-recommended (>= 2013.20130512); however:
  Package texlive-fonts-recommended is not configured yet.
 texlive depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package texlive (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-bibtex-extra:
 texlive-bibtex-extra depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.
 texlive-bibtex-extra depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package texlive-bibtex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-extra:
 texlive-fonts-extra depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-fonts-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-extra-doc:
 texlive-fonts-extra-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-fonts-extra-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-recommended-doc:
 texlive-fonts-recommended-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-fonts-recommended-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-formats-extra:
 texlive-formats-extra depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.
 texlive-formats-extra depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package texlive-formats-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-polish:
 texlive-lang-polish depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.
 texlive-lang-polish depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-polish (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-generic-extra:
 texlive-generic-extra depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-generic-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-indic:
 texlive-lang-indic depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-indic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-spanish:
 texlive-lang-spanish depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-spanish (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-omega:
 texlive-omega depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.
 texlive-omega depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-omega (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-cyrillic:
 texlive-lang-cyrillic depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.
 texlive-lang-cyrillic depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package texlive-lang-cyrillic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-humanities-doc:
 texlive-humanities-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-humanities-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-english:
 texlive-lang-english depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-english (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fragmaster:
 fragmaster depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 fragmaster depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
 fragmaster depends on texlive-extra-utils; however:
  Package texlive-extra-utils is not configured yet.
 fragmaster depends on texlive-font-utils; however:
  Package texlive-font-utils is not configured yet.

dpkg: error processing package fragmaster (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-extra-doc:
 texlive-latex-extra-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-latex-extra-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-publishers-doc:
 texlive-publishers-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-publishers-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-european:
 texlive-lang-european depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-european (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
 tex-common
 latex-sanskrit
 lmodern
 tex-gyre
 texlive-latex-base
 texlive-generic-recommended
 texlive-pstricks
 asymptote
 texlive-latex-recommended
 cm-super-minimal
 cm-super
 texlive-metapost
 context
 context-modules
 texlive-font-utils
 texlive-extra-utils
 feynmf
 latex-xcolor
 latex-beamer
 latex-cjk-common
 latex-cjk-chinese
 latex-cjk-japanese
 latex-cjk-korean
 texlive-lang-other
 latex-cjk-thai
 latex-cjk-all
 latexmk
 m-tx
 musixtex
 pmx
 purifyeps
 rubber
 texlive-fonts-recommended
 texlive
 texlive-bibtex-extra
 texlive-fonts-extra
 texlive-fonts-extra-doc
 texlive-fonts-recommended-doc
 texlive-formats-extra
 texlive-lang-polish
 texlive-generic-extra
 texlive-lang-indic
 texlive-lang-spanish
 texlive-omega
 texlive-lang-cyrillic
 texlive-humanities-doc
 texlive-lang-english
 fragmaster
 texlive-latex-extra-doc
 texlive-publishers-doc
 texlive-lang-european
Processing was halted because there were tE: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up libcdt5 (2.36.0-0ubuntu3) ...
Setting up libcgraph6 (2.36.0-0ubuntu3) ...
Setting up linux-headers-3.13.0-34 (3.13.0-34.60) ...
Setting up libgvc6 (2.36.0-0ubuntu3) ...
Setting up tex-common (4.04) ...
Ignoring /etc/texmf/texmf.d/05TeXMF.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/15Plain.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/45TeXinputs.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/55Fonts.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/65BibTeX.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/75DviPS.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/80DVIPDFMx.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/85Misc.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/90TeXDoc.cnf during generation of texmf.cnf, please remove manually!
Ignoring /etc/texmf/texmf.d/95NonPath.cnf during generation of texmf.cnf, please remove manually!
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... 
updmap-sys failed. Output has been stored in
/tmp/updmap.ADubI9rw
Please include this file if you report a bug.

Sometimes, not accepting conffile updates in /etc/texmf/updmap.d
causes updmap-sys to fail.  Please check for files with extension
.dpkg-dist or .ucf-dist in this directory

dpkg: error processing package tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-omega:
 texlive-omega depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-omega (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-french:
 texlive-lang-french depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-french (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-other:
 texlive-lang-other depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-other (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-publishers:
 texlive-publishers depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-publishers (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-cyrillic:
 texlive-lang-cyrillic depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-cyrillic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-metapost:
 texlive-metapost depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-metapost (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-german:
 texlive-lang-german depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-german (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tex-gyre:
 tex-gyre depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package tex-gyre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-science:
 texlive-science depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-science (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-extra-doc:
 texlive-latex-extra-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-latex-extra-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-science-doc:
 texlive-science-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-science-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-extra-doc:
 texlive-fonts-extra-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-fonts-extra-doc (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-3.13.0-34-generic (3.13.0-34.60) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-27-generic
Found initrd image: /boot/initrd.img-3.13.0-27-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
dpkg: dependency problems prevent configuration of texlive-lang-english:
 texlive-lang-english depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-english (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of context-modules:
 context-modules depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package context-modules (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-european:
 texlive-lang-european depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-european (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-humanities-doc:
 texlive-humanities-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-humanities-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-metapost-doc:
 texlive-metapost-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-metapost-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-luatex:
 texlive-luatex depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-luatex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-generic-recommended:
 texlive-generic-recommended depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-generic-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pstricks-doc:
 texlive-pstricks-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-pstricks-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-recommended:
 texlive-fonts-recommended depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-fonts-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-xcolor:
 latex-xcolor depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package latex-xcolor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pictures:
 texlive-pictures depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-pictures (--configure):
 dependency problems - leaving unconfigured
Setting up libgvpr2 (2.36.0-0ubuntu3) ...
dpkg: dependency problems prevent configuration of texlive-fonts-extra:
 texlive-fonts-extra depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-fonts-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of context:
 context depends on texlive-metapost (>= 2013); however:
  Package texlive-metapost is not configured yet.
 context depends on tex-gyre; however:
  Package tex-gyre is not configured yet.
 context depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.

dpkg: error processing package context (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pictures-doc:
 texlive-pictures-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-pictures-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pmx:
 pmx depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.

dpkg: error processing package pmx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of asymptote:
 asymptote depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package asymptote (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-cjk-japanese:
 latex-cjk-japanese depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.

dpkg: error processing package latex-cjk-japanese (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-formats-extra:
 texlive-formats-extra depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-formats-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of m-tx:
 m-tx depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.

dpkg: error processing package m-tx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-bibtex-extra:
 texlive-bibtex-extra depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-bibtex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-cjk-korean:
 latex-cjk-korean depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.

dpkg: error processing package latex-cjk-korean (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-music:
 texlive-music depends on m-tx; however:
  Package m-tx is not configured yet.
 texlive-music depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.
 texlive-music depends on pmx; however:
  Package pmx is not configured yet.

dpkg: error processing package texlive-music (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended-doc:
 texlive-latex-recommended-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-latex-recommended-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-spanish:
 texlive-lang-spanish depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-spanish (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pstricks:
 texlive-pstricks depends on texlive-generic-recommended (>= 2013.20130512); however:
  Package texlive-generic-recommended is not configured yet.
 texlive-pstricks depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-pstricks (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-african:
 texlive-lang-african depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-african (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-humanities:
 texlive-humanities depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-humanities (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-math-extra:
 texlive-math-extra depends on texlive-fonts-recommended (>= 2013.20130512); however:
  Package texlive-fonts-recommended is not configured yet.
 texlive-math-extra depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-math-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-arabic:
 texlive-lang-arabic depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-arabic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-cjk:
 texlive-lang-cjk depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-cjk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-full:
 texlive-full depends on texlive-lang-spanish (>= 2013.20130512); however:
  Package texlive-lang-spanish is not configured yet.
 texlive-full depends on texlive-omega (>= 2013.20130512); however:
  Package texlive-omega is not configured yet.
 texlive-full depends on texlive-lang-cyrillic (>= 2013.20130512); however:
  Package texlive-lang-cyrillic is not configured yet.
 texlive-full depends on texlive-humanities-doc (>= 2013.20130512); however:
  Package texlive-humanities-doc is not configured yet.
 texlive-full depends on texlive-lang-english (>= 2013.20130512); however:
  Package texlive-lang-english is not configured yet.
 texlive-full depends on texlive-latex-extra-doc (>= 2013.20130512); however:
  Package texlive-latex-extra-doc is not configured yet.
 texlive-full depends on texlive-lang-european (>= 2013.20130512); however:
  Package texlive-lang-european is not configured yet.
 texlive-full depends on texlive-pictures-doc (>= 2013.201305
dpkg: error processing package texlive-full (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tipa:
 tipa depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package tipa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-czechslovak:
 texlive-lang-czechslovak depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.
 texlive-lang-czechslovak depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-czechslovak (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-italian:
 texlive-lang-italian depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-italian (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-portuguese:
 texlive-lang-portuguese depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-portuguese (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-recommended-doc:
 texlive-fonts-recommended-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-fonts-recommended-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Processing triggers for libc-bin (2.19-0ubuntu6.1) ...
Errors were encountered while processing:
 tex-common
 texlive-omega
 texlive-lang-french
 texlive-lang-other
 texlive-publishers
 texlive-lang-cyrillic
 texlive-metapost
 texlive-lang-german
 tex-gyre
 texlive-science
 texlive-latex-extra-doc
 texlive-science-doc
 texlive-fonts-extra-doc
 texlive-lang-english
 context-modules
 texlive-lang-european
 texlive-humanities-doc
 texlive-metapost-doc
 texlive-luatex
 texlive-generic-recommended
 texlive-pstricks-doc
 texlive-fonts-recommended
 latex-xcolor
 texlive-pictures
 texlive-fonts-extra
 context
 texlive-pictures-doc
 pmx
 asymptote
 latex-cjk-japanese
 texlive-formats-extra
 m-tx
 texlive-bibtex-extra
 latex-cjk-korean
 texlive-music
 texlive-latex-recommended-doc
 texlive-lang-spanish
 texlive-latex-recommended
 texlive-pstricks
 texlive-lang-african
 texlive-humanities
 texlive-math-extra
 texlive-lang-arabic
 texlive-lang-cjk
 texlive-full
 tipa
 texlive-latex-base
 texlive-lang-czechslovak
 texlive-lang-italian
 texlive-lang-portuguese
 texlive-fonts-recommended-doc
Processing was halted because there were too many errors.


```

Log from terminal
sudo apt-get update && sudo apt-get upgrade

```
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cm-super:No apport report written because MaxReports is reached already

 cm-super depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.
 cm-super depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
 cm-super depends on cm-super-minimal (= 0.3.4-9); however:
  Package cm-super-minimal is not configured yet.

dpkg: error processing package cm-super (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-metapost:No apport report written because MaxReports is reached already

 texlive-metapost depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-metapost (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of context:No apport report written because MaxReports is reached already

 context depends on texlive-metapost (>= 2013); however:
  Package texlive-metapost is not configured yet.
 context depends on lmodern (>= 2.004.4); however:
  Package lmodern is not configured yet.
 context depends on tex-gyre; however:
  Package tex-gyre is not configured yet.
 context depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.

dpkg: error processing package context (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of context-modules:No apport report written because MaxReports is reached already

 context-modules depends on context (>> 2011); however:
  Package context is not configured yet.
 context-modules depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package context-modules (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-font-utils:No apport report written because MaxReports is reached already

 texlive-font-utils depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-font-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-extra-utils:No apport report written because MaxReports is reached already

 texlive-extra-utils depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.
 texlive-extra-utils depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package texlive-extra-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of feynmf:No apport report written because MaxReports is reached already

 feynmf depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.
 feynmf depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 feynmf depends on texlive-font-utils; however:
  Package texlive-font-utils is not configured yet.
 feynmf depends on texlive-extra-utils; however:
  Package texlive-extra-utils is not configured yet.

dpkg: error processing package feynmf (--configure):
 dependency problems - leaving unconfigured
Setting up graphviz (2.36.0-0ubuntu3) ...No apport report written because MaxReports is reached already

dpkg: dependency problems prevent configuration of latex-xcolor:
 latex-xcolor depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
 latex-xcolor depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package latex-xcolor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-beamer:
 latex-beamer depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.
 latex-beamer depends on latex-xcolor (>= 2.00-1); however:
  Package latex-xcolor is not configured yet.
 latex-beamer depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package latex-beamer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-cjk-common:
 latex-cjk-common depends on texlive-latex-base; however:
  Package texNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                 No apport report written because MaxReports is reached already
                                    No apport report written because MaxReports is reached already
                       No apport report written because MaxReports is reached already
          No apport report written because MaxReports is reached already
                                                                        No apport report written because MaxReports is reached already
                                                           No apport report written because MaxReports is reached already
                                              No apport report written because MaxReports is reached already
                                 live-latex-base is not configured yet.
 latex-cjk-common depends on texlive-font-utils (>= 2007.dfsg.2-1); however:
  Package texlive-font-utils is not configured yet.
 latex-cjk-common depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.

dpkg: error processing package latex-cjk-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-cjk-chinese:
 latex-cjk-chinese depends on latex-cjk-common (= 4.8.3+git20120914-2ubuntu1); however:
  Package latex-cjk-common is not configured yet.
 latex-cjk-chinese depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package latex-cjk-chinese (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-cjk-japanese:
 latex-cjk-japanese depends on latex-cjk-common (= 4.8.3+git20120914-2ubuntu1); however:
  Package latex-cjk-common is not configured yet.
 latex-cjk-japanese depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.

dpkg: error processing package latex-cjk-japanese (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-cjk-korean:
 latex-cjk-korean depends on latex-cjk-common (>= 4.8.3+git20120914-2ubuntu1); however:
  Package latex-cjk-common is not configured yet.
 latex-cjk-korean depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.

dpkg: error processing package latex-cjk-korean (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-other:
 texlive-lang-other depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-other (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-cjk-thai:
 latex-cjk-thai depends on latex-cjk-common (>= 4.8.3+git20120914-2ubuntu1); however:
  Package latex-cjk-common is not configured yet.
 latex-cjk-thai depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 latex-cjk-thai depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.
 latex-cjk-thai depends on texlive-lang-other (>= 2013.20130523-1); however:
  Package texlive-lang-other is not configured yet.

dpkg: error processing package latex-cjk-thai (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-cjk-all:
 latex-cjk-all depends on latex-cjk-common (>= 4.8.3+git20120914-2ubuntu1); however:
  Package latex-cjk-common is not configured yet.
 latex-cjk-all depends on latex-cjk-chinese (>= 4.8.3+git20120914-2ubuntu1); however:
  Package latex-cjk-chinese is not configured yet.
 latex-cjk-all depends on latex-cjk-japanese (>= 4.8.3+git20120914-2ubuntu1); however:
  Package latex-cjk-japanese is not configured yet.
 latex-cjk-all depends on latex-cjk-korean (= 4.8.3+git20120914-2ubuntu1); however:
  Package latex-cjk-korean is not configured yet.
 latex-cjk-all depends on latex-cjk-thai (= 4.8.3+git20120914-2ubuntu1); however:
  Package latex-cjk-thai is not configured yet.

dpkg: error processing package latex-cjk-all (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latexmk:
 latexmk depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package latexmk (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-extra-3.13.0-34-generic (3.13.0-34.60) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-3.13.0-34-generic
) points to /boot/initrd.img-3.13.0-34-generic
 (/boot/initrd.img-3.13.0-34-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-extra-3.13.0-34-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-3.13.0-34-generic
) points to /boot/vmlinuz-3.13.0-34-generic
 (/boot/vmlinuz-3.13.0-34-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-extra-3.13.0-34-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-27-generic
Found initrd image: /boot/initrd.img-3.13.0-27-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-generic (3.13.0.34.40) ...
Setting up linux-headers-3.13.0-34-generic (3.13.0-34.60) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
Setting up linux-headers-generic (3.13.0.34.40) ...
Setting up linux-generic (3.13.0.34.40) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                 No apport report written because MaxReports is reached already
                                    No apport report written because MaxReports is reached already
                       No apport report written because MaxReports is reached already
          No apport report written because MaxReports is reached already
                                                                        No apport report written because MaxReports is reached already
                                                           No apport report written because MaxReports is reached already
                                              No apport report written because MaxReports is reached already
                                 No apport report written because MaxReports is reached already
                    No apport report written because MaxReports is reached already
       No apport report written because MaxReports is reached already
                                                                     No apport report written because MaxReports is reached already
                                                        No apport report written because MaxReports is reached already
                                           No apport report written because MaxReports is reached already
                              No apport report written because MaxReports is reached already
                 No apport report written because MaxReports is reached already
    No apport report written because MaxReports is reached already
                                                                  No apport report written because MaxReports is reached already
                                                     No apport report written because MaxReports is reached already
                                        No apport report written because MaxReports is reached already
                           No apport report written because MaxReports is reached already
              No apport report written because MaxReports is reached already
 No apport report written because MaxReports is reached already
                                                               dpkg: dependency problems prevent configuration of m-tx:
 m-tx depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.

dpkg: error processing package m-tx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of musixtex:
 musixtex depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.

dpkg: error processing package musixtex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pmx:
 pmx depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.
 pmx depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package pmx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of purifyeps:
 purifyeps depends on texlive-metapost; however:
  Package texlive-metapost is not configured yet.

dpkg: error processing package purifyeps (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rubber:
 rubber depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package rubber (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-recommended:
 texlive-fonts-recommended depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-fonts-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive:
 texlive depends on texlive-latex-recommended (>= 2013.20130512); however:
  Package texlive-latex-recommended is not configured yet.
 texlive depends on texlive-fonts-recommended (>= 2013.20130512); however:
  Package texlive-fonts-recommended is not configured yet.
 texlive depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package texlive (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-bibtex-extra:
 texlive-bibtex-extra depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.
 texlive-bibtex-extra depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package texlive-bibtex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-extra:
 texlive-fonts-extra depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-fonts-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-extra-doc:
 texlive-fonts-extra-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-fonts-extra-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-recommended-doc:
 texlive-fonts-recommended-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-fonts-recommended-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-formats-extra:
 texlive-formats-extra depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.
 texlive-formats-extra depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package texlive-formats-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-polish:
 texlive-lang-polish depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.
 texlive-lang-polish depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-polish (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-generic-extra:
 texlive-generic-extra depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-generic-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-indic:
 texlive-lang-indic depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-indic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-spanish:
 texlive-lang-spanish depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-spanish (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-omega:
 texlive-omega depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.
 texlive-omega depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-omega (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-cyrillic:
 texlive-lang-cyrillic depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.
 texlive-lang-cyrillic depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package texlive-lang-cyrillic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-humanities-doc:
 texlive-humanities-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-humanities-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-english:
 texlive-lang-english depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-english (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fragmaster:
 fragmaster depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 fragmaster depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
 fragmaster depends on texlive-extra-utils; however:
  Package texlive-extra-utils is not configured yet.
 fragmaster depends on texlive-font-utils; however:
  Package texlive-font-utils is not configured yet.

dpkg: error processing package fragmaster (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-extra-doc:
 texlive-latex-extra-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-latex-extra-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-publishers-doc:
 texlive-publishers-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-publishers-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-european:
 texlive-lang-european depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-european (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
 tex-common
 latex-sanskrit
 lmodern
 tex-gyre
 texlive-latex-base
 texlive-generic-recommended
 texlive-pstricks
 asymptote
 texlive-latex-recommended
 cm-super-minimal
 cm-super
 texlive-metapost
 context
 context-modules
 texlive-font-utils
 texlive-extra-utils
 feynmf
 latex-xcolor
 latex-beamer
 latex-cjk-common
 latex-cjk-chinese
 latex-cjk-japanese
 latex-cjk-korean
 texlive-lang-other
 latex-cjk-thai
 latex-cjk-all
 latexmk
 m-tx
 musixtex
 pmx
 purifyeps
 rubber
 texlive-fonts-recommended
 texlive
 texlive-bibtex-extra
 texlive-fonts-extra
 texlive-fonts-extra-doc
 texlive-fonts-recommended-doc
 texlive-formats-extra
 texlive-lang-polish
 texlive-generic-extra
 texlive-lang-indic
 texlive-lang-spanish
 texlive-omega
 texlive-lang-cyrillic
 texlive-humanities-doc
 texlive-lang-english
 fragmaster
 texlive-latex-extra-doc
 texlive-publishers-doc
 texlive-lang-european
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

