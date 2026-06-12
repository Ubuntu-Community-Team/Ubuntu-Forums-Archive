---
title: "Can't get openssh-client and openssh-server installed"
date: 2015-02-24
forum: Installation &amp; Upgrades
---

### Post by msoftprogramming on 2015-02-24
Hello,
I am just trying to install openssh-client and openssh-server on my Ubuntu 14.04 machine.

When I do

```

sudo apt-get install openssh-client

```

I get the following:
```

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
/tmp/updmap.4HjOu2Gb
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


dpkg: error processing package cm-super-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cm-super:
 cm-super depends on tex-common (>= 3); No apport report written because MaxReports is reached already
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
                          however:
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
  Package texlive-metapost is not configured yet.
 context depends on lmodern (>= 2.004.4); however:
  Package lmodern is not configured yet.
 context depends on tex-gyre; however:
  Package tex-gyre is not configured yet.
 contNo apport report written because MaxReports is reached already
                                                                   No apport report written because MaxReports is reached already
                                                                                                                                 No apport report written because MaxReports is reached already
                                                                                                                                                                                               No apport report written because MaxReports is reached already
                                                No apport report written because MaxReports is reached already
                                                                                                              No apport report written because MaxReports is reached already
                                                                                                                                                                            No apport report written because MaxReports is reached already
                             No apport report written because MaxReports is reached already
                                                                                           No apport report written because MaxReports is reached already
                                                                                                                                                         ext depends on tex-common (>= 4); however:
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
  Package tex-common is not cNo apport report written because MaxReports is reached already
                                                                                           No apport report written because MaxReports is reached already
                                                                                                                                                         onfigured yet.
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
 dependency problems - lNo apport report written because MaxReports is reached already
                                                                                      eaving unconfigured
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
dpkg: dependency problems prevent configuration of texlive-fonts-recommended:
 texlive-fonts-recommended depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-fonts-recommended (--configure):
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
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-humanities-doc:
 texlive-humanities-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-humanities-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-english:
No apport report written because MaxReports is reached already
                                                               texlive-lang-english depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-lang-english (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
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
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-latex-extra-doc:
 texlive-latex-extra-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-latex-extra-doc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-publishers-doc:
 texlive-publishers-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-publishers-doc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-lang-european:
 texlive-lang-european depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-lang-european (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-pictures-doc:
 texlive-pictures-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-pictures-doc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-metapost-doc:
 texlive-metapost-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-metapost-doc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-science-doc:
 texlive-science-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-science-doc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-lang-african:
 texlive-lang-african depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-lang-african (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-math-extra:
 texlive-math-extra depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.
 texlive-math-extra depends on texlive-fonts-recommended (>= 2013.20130512); however:
  Package texlive-fonts-recommended is not configured yet.
 texlive-math-extra depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.


dpkg: error processing package texlive-math-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stoppingNo apport report written because MaxReports is reached already


Errors were encountered while processing:
 tex-common
 latex-sanskrit
 lmodern
 tex-gyre
 texlive-latex-base
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
 texlive-bibtex-extra
 texlive-fonts-extra
 texlive-fonts-extra-doc
 texlive-fonts-recommended
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
 texlive-pictures-doc
 texlive-metapost-doc
 texlive-science-doc
 texlive-lang-african
 texlive-math-extra
ProcessingE: Sub-process /usr/bin/dpkg returned an error code (1)

```

I really have no idea on what is going on. Can somebody please help?

Thank you very much indeed.

Matteo

---

### Post by TheFu on 2015-02-25
Update the system first.  It is likely your dependencies haven't been refreshed in a long time.
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs) - weekly patching is recommended.```
sudo aptitude update; sudo aptitude full-upgrade
```

You can use **apt-get dist-upgrade**, if you like.

---

