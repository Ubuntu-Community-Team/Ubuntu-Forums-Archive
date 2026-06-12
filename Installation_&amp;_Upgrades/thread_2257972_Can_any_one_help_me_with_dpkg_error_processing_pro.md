---
title: "Can any one help me with dpkg error processing problems?"
date: 2014-12-23
forum: Installation &amp; Upgrades
---

### Post by gor4l on 2014-12-23
I can`t run update :(
```
                                                              dpkg: dependency problems prevent configuration of texlive-pstricks:
 texlive-pstricks depends on texlive-generic-recommended (>= 2013.20130512); however:
  Package texlive-generic-recommended is not configured yet.
 texlive-pstricks depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-pstricks (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of asymptote:
 asymptote depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 asymptote depends on texlive-pstricks; however:
  Package texlive-pstricks is not configured yet.
 asymptote depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package asymptote (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.
 texlive-latex-recommended depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of cm-super-minimal:
 cm-super-minimal depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.
 cm-super-minimal depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.

dpkg: error processing package cm-super-minimal (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of cm-super:
 cm-super depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.
 cm-super depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
 cm-super depends on cm-super-minimal (= 0.3.4-9); however:
  Package cm-super-minimal is not configured yet.

dpkg: error processing package cm-super (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive-metapost:
 texlive-metapost depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-metapost (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of context:
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
dpkg: dependency problems prevent configuration of latex-xcolor:No apport report written because MaxReports is reached already

 latex-xcolor depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
 latex-xcolor depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package latex-xcolor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-beamer:No apport report written because MaxReports is reached already

 latex-beamer depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.
 latex-beamer depends on latex-xcolor (>= 2.00-1); however:
  Package latex-xcolor is not configured yet.
 latex-beamer depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package latex-beamer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-cjk-common:No apport report written because MaxReports is reached already

 latex-cjk-common depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 latex-cjk-common depends on texlive-font-utils (>= 2007.dfsg.2-1); however:
  Package texlive-font-utils is not configured yet.
 latex-cjk-common depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.

dpkg: error processing package latex-cjk-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-cjk-chinese:No apport report written because MaxReports is reached already

 latex-cjk-chinese depends on latex-cjk-common (= 4.8.3+git20120914-2ubuntu1); however:
  Package latex-cjk-common is not configured yet.
 latex-cjk-chinese depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package latex-cjk-chinese (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-cjk-japanese:No apport report written because MaxReports is reached already

 latex-cjk-japanese depends on latex-cjk-common (= 4.8.3+git20120914-2ubuntu1); however:
  Package latex-cjk-common is not configured yet.
 latex-cjk-japanese depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.

dpkg: error processing package latex-cjk-japanese (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-cjk-korean:No apport report written because MaxReports is reached already

 latex-cjk-korean depends on latex-cjk-common (>= 4.8.3+git20120914-2ubuntu1); however:
  Package latex-cjk-common is not configured yet.
 latex-cjk-korean depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.

dpkg: error processing package latex-cjk-korean (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-other:No apport report written because MaxReports is reached already

 texlive-lang-other depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-other (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-cjk-thai:No apport report written because MaxReports is reached already

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
dpkg: dependency problems prevent configuration of latex-cjk-all:No apport report written because MaxReports is reached already

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
dpkg: dependency problems prevent configuration of latexmk:No apport report written because MaxReports is reached already

 latexmk depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package latexmk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of m-tx:No apport report written because MaxReports is reached already

 m-tx depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.

dpkg: error processing package m-tx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of musixtex:No apport report written because MaxReports is reached already

 musixtex depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.

dpkg: error processing package musixtex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pmx:No apport report written because MaxReports is reached already

 pmx depends on tex-common (>= 4); however:
  Package tex-common is not configured yet.
 pmx depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package pmx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of purifyeps:No apport report written because MaxReports is reached already

 purifyeps depends on texlive-metapost; however:
  Package texlive-metapost is not configured yet.

dpkg: error processing package purifyeps (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rubber:No apport report written because MaxReports is reached already

 rubber depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package rubber (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-recommended:No apport report written because MaxReports is reached already

 texlive-fonts-recommended depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-fonts-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive:No apport report written because MaxReports is reached already

 texlive depends on texlive-latex-recommended (>= 2013.20130512); however:
  Package texlive-latex-recommended is not configured yet.
 texlive depends on texlive-fonts-recommended (>= 2013.20130512); however:
  Package texlive-fonts-recommended is not configured yet.
 texlive depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package texlive (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-bibtex-extra:No apport report written because MaxReports is reached already

 texlive-bibtex-extra depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.
 texlive-bibtex-extra depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package texlive-bibtex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-extra:No apport report written because MaxReports is reached already

 texlive-fonts-extra depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-fonts-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-extra-doc:No apport report written because MaxReports is reached already

 texlive-fonts-extra-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-fonts-extra-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-recommended-doc:No apport report written because MaxReports is reached already

 texlive-fonts-recommended-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-fonts-recommended-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-formats-extra:No apport report written because MaxReports is reached already

 texlive-formats-extra depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.
 texlive-formats-extra depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package texlive-formats-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-polish:No apport report written because MaxReports is reached already

 texlive-lang-polish depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.
 texlive-lang-polish depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-polish (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-generic-extra:No apport report written because MaxReports is reached already

 texlive-generic-extra depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-generic-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-indic:No apport report written because MaxReports is reached already

 texlive-lang-indic depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-indic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-spanish:No apport report written because MaxReports is reached already

 texlive-lang-spanish depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-spanish (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-omega:No apport report written because MaxReports is reached already

 texlive-omega depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.
 texlive-omega depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-omega (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-cyrillic:No apport report written because MaxReports is reached already

 texlive-lang-cyrillic depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.
 texlive-lang-cyrillic depends on texlive-latex-base (>= 2013.20130512); however:
  Package texlive-latex-base is not configured yet.

dpkg: error processing package texlive-lang-cyrillic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-humanities-doc:No apport report written because MaxReports is reached already

 texlive-humanities-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-humanities-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-english:No apport report written because MaxReports is reached already

 texlive-lang-english depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-english (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fragmaster:No apport report written because MaxReports is reached already

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
dpkg: dependency problems prevent configuration of texlive-latex-extra-doc:No apport report written because MaxReports is reached already

 texlive-latex-extra-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-latex-extra-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-publishers-doc:No apport report written because MaxReports is reached already

 texlive-publishers-doc depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-publishers-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-lang-european:No apport report written because MaxReports is reached already

 texlive-lang-european depends on tex-common (>= 3); however:
  Package tex-common is not configured yet.

dpkg: error processing package texlive-lang-european (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
No apport report written because MaxReports is reached already
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

### Post by nerdtron on 2014-12-23
What were you trying to do before this? are compiling/installing another software? we'll need more info than just this.

---

### Post by Impavidus on 2014-12-24
It would have helped if you had provided the command that generated all those errors and had told us what you had done before that could have caused the error.

It seems there are a lot of packages that cannot be configured because tex-common, texlive-latex-base and some others have not been configured. Maybe it can be fixed using```
sudo dpkg --configure -a
```If not, show the output in code tags.

Edit: I see that all packages reported as unconfigured depend directly or indirectly on tex-common, except tex-common itself, which depends on none of the mentioned packages. Configuring tex-common and then all others should fix the issue.

---

### Post by gor4l on 2014-12-24
Thanks for quick reply.
I think this happened before or after this
[http://ubuntuforums.org/showthread.php?t=2241460](http://ubuntuforums.org/showthread.php?t=2241460)
Since then I can`t update system.
log from 
```
sudo apt-get --configure -a
```
```
~$ sudo dpkg --configure -a
[sudo] password: 
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
/tmp/updmap.Q4bP53aK
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


```
$ sudo dpkg --configure tex-common
```

```
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
/tmp/updmap.G4Q5e8pU
Please include this file if you report a bug.

Sometimes, not accepting conffile updates in /etc/texmf/updmap.d
causes updmap-sys to fail.  Please check for files with extension
.dpkg-dist or .ucf-dist in this directory

dpkg: error processing package tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 tex-common
```

---

### Post by Impavidus on 2014-12-24
On a typical TexLive installation on Ubuntu 14.04 (like mine, more or less), /etc/texmf/texmf.d/ only contains a single file (00debian.cnf), so that's a bit peculiar on your system, but it's not what causes the error. The problem is updmap-sys failing, possibly because of a problem in /etc/texmf/updmap.d/. In other words, something is broken in your TeX font configuration. By default, that directory is empty.

Unfortunately, I have only dealt with updmap-sys and /etc/texmf/updmap.d once, and that already makes me a TeX hacker. Have you ever installed TeX fonts or symbol sets not coming from the Ubuntu repositories? They might be related. The error message mentions a log file named /tmp/updmap.Q4bP53aK. Anything interesting in there?

---

### Post by oldos2er on 2014-12-24
Edited title. It helps to create a thread title that outlines your problem or question. Your original title - Can anyone help me? - is easily answered: yes.  :)

---

### Post by gor4l on 2014-12-26
> Have you ever installed TeX fonts or symbol sets not coming from the  Ubuntu repositories? 
Yes, few fonts - as far I can remember.
In .fonts folder I have calibri.ttf and CALIBRI.TTF
> The error message mentions a  log file named /tmp/updmap.Q4bP53aK. Anything interesting in there?                 
I don`t have updmap.Q4bP53aK file.


________________
Thanks 
     [**[COLOR=#C61919][B]oldos2er**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=338320")

---

### Post by Impavidus on 2014-12-26
> **gor4l said:**
> Yes, few fonts - as far I can remember.
In .fonts folder I have calibri.ttf and CALIBRI.TTFThose must be unrelated. TeX fonts are managed completely separate from other fonts.

> I don`t have updmap.Q4bP53aK file.


________________
Thanks 
     [**[COLOR=#C61919][B]oldos2er**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=338320")

It may have been deleted during a reboot. That usually happens to files in /tmp. If you try to configure tex-common again it should mention a new filename where the details should be stored.
You may also call **sudo updmap-sys** yourself. It might give some more diagnostics. Or try digging into /etx/texmf/updmap.d/ and see if there is anything familiar.

What strikes me is that most people are content with the way their package manager handles updmap and related stuff. You need to be quite a TeX hacker to do it yourself. I once did, creating a brand new script, and it took me a week to figure out how it worked. If you tried tweaking anything there, you would have remembered. Or you ran some kind of install script that didn't do a very good job.

If you didn't apply a lot of tweaks to your TeX installation, it may be easiest if you uninstall it, remove any remaining files and directories belonging to it (like /etc/texmf, /usr/share/tex*) and reinstall.

It's past 1AM here. Think I need some sleep now.

---

### Post by gor4l on 2014-12-27
```
sudo apt-get update && sudo apt-get upgrade
```
updmap.XLnx31yw
```
updmap: resetting $HOME value (was /home/marcingorski) to root's actual home (/root).
updmap is using the following updmap.cfg files (in precedence order):
  /var/lib/texmf/web2c/updmap.cfg
  /usr/share/texmf/web2c/updmap.cfg
  /usr/share/texlive/texmf-dist/web2c/updmap.cfg
updmap is using the following updmap.cfg file for writing changes:
  /etc/texmf/web2c/updmap.cfg
dvips output dir: "/var/lib/texmf/fonts/map/dvips/updmap"
pdftex output dir: "/var/lib/texmf/fonts/map/pdftex/updmap"
dvipdfmx output dir: "/var/lib/texmf/fonts/map/dvipdfmx/updmap"

ERROR:  The following map file(s) couldn't be found:
    antp.map (in /var/lib/texmf/web2c/updmap.cfg)
    comicvn.map (in /var/lib/texmf/web2c/updmap.cfg)
    csother.map (in /var/lib/texmf/web2c/updmap.cfg)
    cstext.map (in /var/lib/texmf/web2c/updmap.cfg)
    fi4.map (in /var/lib/texmf/web2c/updmap.cfg)
    grverb.map (in /var/lib/texmf/web2c/updmap.cfg)
    mscorevn.map (in /var/lib/texmf/web2c/updmap.cfg)
    slantcm.map (in /var/lib/texmf/web2c/updmap.cfg)
    zpeu.map (in /var/lib/texmf/web2c/updmap.cfg)

    Did you run mktexlsr?

    You can disable non-existent map entries using the option
      --syncwithtrees.

```
```
sudo dpkg --configure -a
```
updmap.CO67HOES
```
updmap: resetting $HOME value (was /home/marcingorski) to root's actual home (/root).
updmap is using the following updmap.cfg files (in precedence order):
  /var/lib/texmf/web2c/updmap.cfg
  /usr/share/texmf/web2c/updmap.cfg
  /usr/share/texlive/texmf-dist/web2c/updmap.cfg
updmap is using the following updmap.cfg file for writing changes:
  /etc/texmf/web2c/updmap.cfg
dvips output dir: "/var/lib/texmf/fonts/map/dvips/updmap"
pdftex output dir: "/var/lib/texmf/fonts/map/pdftex/updmap"
dvipdfmx output dir: "/var/lib/texmf/fonts/map/dvipdfmx/updmap"

ERROR:  The following map file(s) couldn't be found:
    antp.map (in /var/lib/texmf/web2c/updmap.cfg)
    comicvn.map (in /var/lib/texmf/web2c/updmap.cfg)
    csother.map (in /var/lib/texmf/web2c/updmap.cfg)
    cstext.map (in /var/lib/texmf/web2c/updmap.cfg)
    fi4.map (in /var/lib/texmf/web2c/updmap.cfg)
    grverb.map (in /var/lib/texmf/web2c/updmap.cfg)
    mscorevn.map (in /var/lib/texmf/web2c/updmap.cfg)
    slantcm.map (in /var/lib/texmf/web2c/updmap.cfg)
    zpeu.map (in /var/lib/texmf/web2c/updmap.cfg)

    Did you run mktexlsr?

    You can disable non-existent map entries using the option
      --syncwithtrees.
```
```
sudo dpkg --configure tex-common
```
updmap.dOH8T3wm
```
updmap: resetting $HOME value (was /home/marcingorski) to root's actual home (/root).
updmap is using the following updmap.cfg files (in precedence order):
  /var/lib/texmf/web2c/updmap.cfg
  /usr/share/texmf/web2c/updmap.cfg
  /usr/share/texlive/texmf-dist/web2c/updmap.cfg
updmap is using the following updmap.cfg file for writing changes:
  /etc/texmf/web2c/updmap.cfg
dvips output dir: "/var/lib/texmf/fonts/map/dvips/updmap"
pdftex output dir: "/var/lib/texmf/fonts/map/pdftex/updmap"
dvipdfmx output dir: "/var/lib/texmf/fonts/map/dvipdfmx/updmap"

ERROR:  The following map file(s) couldn't be found:
    antp.map (in /var/lib/texmf/web2c/updmap.cfg)
    comicvn.map (in /var/lib/texmf/web2c/updmap.cfg)
    csother.map (in /var/lib/texmf/web2c/updmap.cfg)
    cstext.map (in /var/lib/texmf/web2c/updmap.cfg)
    fi4.map (in /var/lib/texmf/web2c/updmap.cfg)
    grverb.map (in /var/lib/texmf/web2c/updmap.cfg)
    mscorevn.map (in /var/lib/texmf/web2c/updmap.cfg)
    slantcm.map (in /var/lib/texmf/web2c/updmap.cfg)
    zpeu.map (in /var/lib/texmf/web2c/updmap.cfg)

    Did you run mktexlsr?

    You can disable non-existent map entries using the option
      --syncwithtrees.
```

```
 sudo mktexlsr
mktexlsr: Updating /usr/local/share/texmf/ls-R... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVEDIST... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.

```

after update and upgrade

```
updmap: resetting $HOME value (was /home/marcingorski) to root's actual home (/root).
updmap is using the following updmap.cfg files (in precedence order):
  /var/lib/texmf/web2c/updmap.cfg
  /usr/share/texmf/web2c/updmap.cfg
  /usr/share/texlive/texmf-dist/web2c/updmap.cfg
updmap is using the following updmap.cfg file for writing changes:
  /etc/texmf/web2c/updmap.cfg
dvips output dir: "/var/lib/texmf/fonts/map/dvips/updmap"
pdftex output dir: "/var/lib/texmf/fonts/map/pdftex/updmap"
dvipdfmx output dir: "/var/lib/texmf/fonts/map/dvipdfmx/updmap"

ERROR:  The following map file(s) couldn't be found:
    antp.map (in /var/lib/texmf/web2c/updmap.cfg)
    comicvn.map (in /var/lib/texmf/web2c/updmap.cfg)
    csother.map (in /var/lib/texmf/web2c/updmap.cfg)
    cstext.map (in /var/lib/texmf/web2c/updmap.cfg)
    fi4.map (in /var/lib/texmf/web2c/updmap.cfg)
    grverb.map (in /var/lib/texmf/web2c/updmap.cfg)
    mscorevn.map (in /var/lib/texmf/web2c/updmap.cfg)
    slantcm.map (in /var/lib/texmf/web2c/updmap.cfg)
    zpeu.map (in /var/lib/texmf/web2c/updmap.cfg)

    Did you run mktexlsr?

    You can disable non-existent map entries using the option
      --syncwithtrees.
```
```
sudo updmap-sys
updmap: resetting $HOME value (was /home/marcingorski) to root's actual home (/root).
updmap is using the following updmap.cfg files (in precedence order):
  /var/lib/texmf/web2c/updmap.cfg
  /usr/share/texmf/web2c/updmap.cfg
  /usr/share/texlive/texmf-dist/web2c/updmap.cfg
updmap is using the following updmap.cfg file for writing changes:
  /etc/texmf/web2c/updmap.cfg
dvips output dir: "/var/lib/texmf/fonts/map/dvips/updmap"
pdftex output dir: "/var/lib/texmf/fonts/map/pdftex/updmap"
dvipdfmx output dir: "/var/lib/texmf/fonts/map/dvipdfmx/updmap"

ERROR:  The following map file(s) couldn't be found:
    antp.map (in /var/lib/texmf/web2c/updmap.cfg)
    comicvn.map (in /var/lib/texmf/web2c/updmap.cfg)
    csother.map (in /var/lib/texmf/web2c/updmap.cfg)
    cstext.map (in /var/lib/texmf/web2c/updmap.cfg)
    fi4.map (in /var/lib/texmf/web2c/updmap.cfg)
    grverb.map (in /var/lib/texmf/web2c/updmap.cfg)
    mscorevn.map (in /var/lib/texmf/web2c/updmap.cfg)
    slantcm.map (in /var/lib/texmf/web2c/updmap.cfg)
    zpeu.map (in /var/lib/texmf/web2c/updmap.cfg)

    Did you run mktexlsr?

    You can disable non-existent map entries using the option
      --syncwithtrees.


```
[IMG]http://i57.tinypic.com/wiasco.png[/IMG]

---

### Post by Impavidus on 2014-12-27
Did you already tell us which Ubuntu release you're running? I don't think so.

To be honest, I don't really know what's going on. Some .cfg files mention certain .map, mapping fonts to font files, but those .map files seem to be missing. Could be an improperly installed package. It might help if you purge all TeX-related packages, make sure everything is gone (and manually delete anything that stays behind, as it was probably manually installed), and then reinstall them.

---

### Post by gor4l on 2014-12-27
> tell us which Ubuntu release you're running
Ubuntu 14.04.1

I do what you tell me. 
Completely delete tex-common and related packages using synaptic.

then I run in terminal
```
sudo apt-get update
[sudo] password: 
Ign http://archive.canonical.com trusty InRelease
Ign http://security.ubuntu.com precise-security InRelease                      
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://security.ubuntu.com precise-security Release.gpg                    
Hit http://archive.canonical.com trusty Release                                
Ign http://pl.archive.ubuntu.com precise InRelease                   
Ign http://extras.ubuntu.com precise InRelease                       
Ign http://pl.archive.ubuntu.com precise-updates InRelease                     
Ign http://pl.archive.ubuntu.com trusty-backports InRelease                    
Hit http://security.ubuntu.com precise-security Release                        
Hit http://pl.archive.ubuntu.com precise Release.gpg                 
Hit http://extras.ubuntu.com precise Release.gpg                     
Hit http://pl.archive.ubuntu.com precise-updates Release.gpg
Hit http://pl.archive.ubuntu.com trusty-backports Release.gpg                  
Hit http://pl.archive.ubuntu.com precise Release                               
Hit http://extras.ubuntu.com precise Release                          
Hit http://pl.archive.ubuntu.com precise-updates Release              
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://pl.archive.ubuntu.com trusty-backports Release                      
Hit http://security.ubuntu.com precise-security/main Sources                   
Hit http://pl.archive.ubuntu.com precise/main Sources                          
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://pl.archive.ubuntu.com precise/restricted Sources                    
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://pl.archive.ubuntu.com precise/universe Sources                      
Hit http://security.ubuntu.com precise-security/restricted Sources             
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit http://pl.archive.ubuntu.com precise/multiverse Sources                    
Hit http://pl.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://extras.ubuntu.com precise/main amd64 Packages             
Hit http://security.ubuntu.com precise-security/universe Sources     
Hit http://pl.archive.ubuntu.com precise/restricted amd64 Packages   
Hit http://pl.archive.ubuntu.com precise/universe amd64 Packages     
Hit http://extras.ubuntu.com precise/main i386 Packages              
Hit http://pl.archive.ubuntu.com precise/multiverse amd64 Packages   
Hit http://security.ubuntu.com precise-security/multiverse Sources
Hit http://pl.archive.ubuntu.com precise/main i386 Packages
Hit http://pl.archive.ubuntu.com precise/restricted i386 Packages    
Hit http://security.ubuntu.com precise-security/main amd64 Packages  
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages
Hit http://pl.archive.ubuntu.com precise/universe i386 Packages
Hit http://pl.archive.ubuntu.com precise/multiverse i386 Packages    
Hit http://security.ubuntu.com precise-security/universe amd64 Packages
Hit http://pl.archive.ubuntu.com precise/main Translation-en         
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages
Hit http://pl.archive.ubuntu.com precise/multiverse Translation-en   
Hit http://security.ubuntu.com precise-security/main i386 Packages   
Hit http://pl.archive.ubuntu.com precise/restricted Translation-en   
Hit http://pl.archive.ubuntu.com precise/universe Translation-en
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://pl.archive.ubuntu.com precise-updates/main Sources        
Hit http://pl.archive.ubuntu.com precise-updates/restricted Sources  
Hit http://pl.archive.ubuntu.com precise-updates/universe Sources    
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://pl.archive.ubuntu.com precise-updates/multiverse Sources
Hit http://pl.archive.ubuntu.com precise-updates/main amd64 Packages
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://pl.archive.ubuntu.com precise-updates/restricted amd64 Packages
Hit http://pl.archive.ubuntu.com precise-updates/universe amd64 Packages
Hit http://pl.archive.ubuntu.com precise-updates/multiverse amd64 Packages
Ign http://extras.ubuntu.com precise/main Translation-en_US
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://pl.archive.ubuntu.com precise-updates/main i386 Packages
Ign http://extras.ubuntu.com precise/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://pl.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://pl.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://pl.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://pl.archive.ubuntu.com precise-updates/main Translation-en
Hit http://pl.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://pl.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://pl.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://pl.archive.ubuntu.com trusty-backports/restricted amd64 Packages
Hit http://security.ubuntu.com precise-security/universe Translation-en
Hit http://pl.archive.ubuntu.com trusty-backports/universe amd64 Packages
Hit http://pl.archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://pl.archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://pl.archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://pl.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://pl.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://pl.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://pl.archive.ubuntu.com trusty-backports/universe Translation-en
Ign http://pl.archive.ubuntu.com precise/main Translation-en_US
Ign http://pl.archive.ubuntu.com precise/multiverse Translation-en_US
Ign http://pl.archive.ubuntu.com precise/restricted Translation-en_US
Ign http://pl.archive.ubuntu.com precise/universe Translation-en_US
Reading package lists... Done

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
~$ 


```

---

### Post by Impavidus on 2014-12-31
OK, the package manager is happy again.

There was something wrong with the way TeX was installed on your system. All those files in your /etc/texmf/updmap.d have names suggesting they belong to the official Ubuntu packages containing TeX (texlive-fonts-recommended, for example), but they don't exist on my system, even though I have a pretty standard TeXLive installation from the repositories including those packages, with just one manual addition in /etc/texmf/updmap.d. So I think you installed it from some kind of broken PPA or did a manual installation. In any case, it was broken.

To remove any manually installed TeX related software, check whether directories like /etc/texmf or /usr/share/tex* (there are several of those, like tex-common, texlive and texmf) have been removed. They should be gone, but may still be there in case something was manually installed. If so, remove them manually. If you installed TeXLive from a PPA, disable it. It appears to have been broken.

You should be able to reinstall TeXLive from the repositories by installing **texlive**. Let's hope the problem does not reappear.

---

