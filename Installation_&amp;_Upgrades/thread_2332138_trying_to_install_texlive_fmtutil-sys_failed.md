---
title: "trying to install texlive: fmtutil-sys failed"
date: 2016-07-28
forum: Installation &amp; Upgrades
---

### Post by neunlemminge on 2016-07-28
Hi,

since a few weeks I am having trouble with my ubuntu 12.04 system. I thought it is caused by texlive, so I removed it and reinstalled it (a few times), but it still does not work. Here is what ```
sudo apt-get install texlive-latex-base
``` gives me:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  lmodern tex-common texlive-base texlive-binaries texlive-common
  texlive-doc-base texlive-latex-base-doc
Suggested packages:
  perl-tk
The following NEW packages will be installed:
  lmodern tex-common texlive-base texlive-binaries texlive-common
  texlive-doc-base texlive-latex-base texlive-latex-base-doc
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/84.6 MB of archives.
After this operation, 163 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
Selecting previously unselected package tex-common.
(Reading database ... 1724127 files and directories currently installed.)
Unpacking tex-common (from .../tex-common_2.10_all.deb) ...
Selecting previously unselected package lmodern.
Unpacking lmodern (from .../lmodern_2.004.1-3.1ubuntu1_all.deb) ...
Selecting previously unselected package texlive-common.
Unpacking texlive-common (from .../texlive-common_2009-15_all.deb) ...
Selecting previously unselected package texlive-doc-base.
Unpacking texlive-doc-base (from .../texlive-doc-base_2009-2_all.deb) ...
Selecting previously unselected package texlive-binaries.
Unpacking texlive-binaries (from .../texlive-binaries_2009-11ubuntu2_amd64.deb) ...
Selecting previously unselected package texlive-base.
Unpacking texlive-base (from .../texlive-base_2009-15_all.deb) ...
Selecting previously unselected package texlive-latex-base.
Unpacking texlive-latex-base (from .../texlive-latex-base_2009-15_all.deb) ...
Selecting previously unselected package texlive-latex-base-doc.
Unpacking texlive-latex-base-doc (from .../texlive-latex-base-doc_2009-15_all.deb) ...
Processing triggers for doc-base ...
Processing 2 added doc-base files...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Processing triggers for fontconfig ...
Processing triggers for install-info ...
Setting up tex-common (2.10) ...

Creating config file /etc/texmf/texmf.d/05TeXMF.cnf with new version

Creating config file /etc/texmf/texmf.d/15Plain.cnf with new version

Creating config file /etc/texmf/texmf.d/45TeXinputs.cnf with new version

Creating config file /etc/texmf/texmf.d/55Fonts.cnf with new version

Creating config file /etc/texmf/texmf.d/65BibTeX.cnf with new version

Creating config file /etc/texmf/texmf.d/75DviPS.cnf with new version

Creating config file /etc/texmf/texmf.d/80DVIPDFMx.cnf with new version

Creating config file /etc/texmf/texmf.d/85Misc.cnf with new version

Creating config file /etc/texmf/texmf.d/90TeXDoc.cnf with new version

Creating config file /etc/texmf/texmf.d/95NonPath.cnf with new version

Creating config file /etc/texmf/updmap.d/00updmap.cfg with new version

Creating config file /etc/texmf/texmf.cnf with new version
Running mktexlsr. This may take some time... done.
texlive-base is not ready, delaying updmap-sys call
texlive-base is not ready, skipping fmtutil-sys --all call
Setting up lmodern (2.004.1-3.1ubuntu1) ...
Setting up texlive-common (2009-15) ...
Setting up texlive-doc-base (2009-2) ...
Setting up texlive-binaries (2009-11ubuntu2) ...
update-alternatives: using /usr/bin/xdvi-xaw to provide /usr/bin/xdvi.bin (xdvi.bin) in auto mode.
update-alternatives: using /usr/bin/bibtex.original to provide /usr/bin/bibtex (bibtex) in auto mode.
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVE... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.
Building format(s) --refresh.
    This may take some time... done.
Setting up texlive-latex-base-doc (2009-15) ...
Processing triggers for tex-common ...
Running mktexlsr. This may take some time... done.
texlive-base is not ready, delaying updmap-sys call
Setting up texlive-base (2009-15) ...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVE... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.

Creating config file /etc/texmf/dvips/config/config.ps with new version

Creating config file /etc/texmf/tex/generic/config/pdftexconfig.tex with new version

Creating config file /etc/texmf/dvipdfmx/dvipdfmx.cfg with new version

Creating config file /etc/texmf/xdvi/XDvi with new version
Replacing config file /etc/texmf/dvips/config/config.ps with new version
Replacing config file /etc/texmf/dvipdfmx/dvipdfmx.cfg with new version
Replacing config file /etc/texmf/xdvi/XDvi with new version
Replacing config file /etc/texmf/tex/generic/config/pdftexconfig.tex with new version
pdftex paper size has changed, refreshing formats
fmtutil: no format depends on engine `pdftex'.
Running mktexlsr. This may take some time... done.
Building format(s) --all --cnffile /etc/texmf/fmt.d/10texlive-base.cnf.
    This may take some time... done.
Processing triggers for tex-common ...
Running updmap-sys. This may take some time... done.
Running mktexlsr /var/lib/texmf ... done.
Building e-tex based formats --byhyphen /var/lib/texmf/tex/generic/config/language.def.
    This may take some time... done.
Setting up texlive-latex-base (2009-15) ...
Running mktexlsr. This may take some time... done.
Building format(s) --all --cnffile /etc/texmf/fmt.d/10texlive-latex-base.cnf.
    This may take some time... 
fmtutil-sys failed. Output has been stored in
/tmp/fmtutil.tKVsWiW1
Please include this file if you report a bug.

dpkg: error processing texlive-latex-base (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for tex-common ...
Running updmap-sys. This may take some time... done.
Running mktexlsr /var/lib/texmf ... done.
Errors were encountered while processing:
 texlive-latex-base
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

/tmp/fmtutil.tKVsWiW1 gives the following:

```

fmtutil: running `pdftex -ini   -jobname=latex -progname=latex -translate-file=c
p227.tcx *latex.ini' ...
This is pdfTeX, Version 3.1415926-1.40.10 (TeX Live 2009/Debian) (INITEX)
 (/usr/share/texmf-texlive/web2c/cp227.tcx)
entering extended mode
(/usr/share/texmf/tex/latex/config/latex.ini
(/etc/texmf/tex/generic/config/pdftexconfig.tex)
(/usr/share/texmf/tex/latex/base/latex.ltx
(/usr/share/texmf/tex/latex/base/texsys.cfg)
./texsys.aux found


\@currdir set to: ./.


Assuming \openin and \input 
have the same search path.


Defining UNIX/DOS style filename parser.

catcodes, registers, compatibility for TeX 2,  parameters,

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
! You are attempting to make a LaTeX format from a source file
! That is more than five years old.
!
! If you enter <return> to scroll past this message then the format
! will be built, but please consider obtaining newer source files
! before continuing to build LaTeX.
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

! LaTeX source files more than 5 years old!.
l.540 ...aTeX source files more than 5 years old!}
                                                  
LaTeX2e <2003/12/01>
hacks, control, par, spacing, files, font encodings, lengths,
====================================

Local config file fonttext.cfg used

====================================
(/usr/share/texmf-texlive/tex/latex/base/fonttext.cfg
(/usr/share/texmf/tex/latex/base/fonttext.ltx
=== Don't modify this file, use a .cfg file instead ===

(/usr/share/texmf/tex/latex/base/omlenc.def)
(/usr/share/texmf/tex/latex/base/t1enc.def)
(/usr/share/texmf/tex/latex/base/ot1enc.def)
(/usr/share/texmf/tex/latex/base/omsenc.def)
(/usr/share/texmf/tex/latex/base/t1cmr.fd)
(/usr/share/texmf/tex/latex/base/ot1cmr.fd)
(/usr/share/texmf/tex/latex/base/ot1cmss.fd)
(/usr/share/texmf/tex/latex/base/ot1cmtt.fd)))
====================================

Local config file fontmath.cfg used

====================================
(/usr/share/texmf-texlive/tex/latex/base/fontmath.cfg
(/usr/share/texmf/tex/latex/base/fontmath.ltx
=== Don't modify this file, use a .cfg file instead ===

(/usr/share/texmf/tex/latex/base/omlcmm.fd)
(/usr/share/texmf/tex/latex/base/omscmsy.fd)
(/usr/share/texmf/tex/latex/base/omxcmex.fd)
(/usr/share/texmf/tex/latex/base/ucmr.fd)))
====================================

Local config file preload.cfg used

=====================================
(/usr/share/texmf-texlive/tex/latex/base/preload.cfg
(/usr/share/texmf/tex/latex/base/preload.ltx)) page nos., x-ref, environments,
center, verbatim, math definitions, boxes, title, sectioning, contents,
floats, footnotes, index, bibliography, output,
===========================================
Local configuration file hyphen.cfg used
===========================================
(/usr/share/texmf-texlive/tex/generic/babel/hyphen.cfg
(/usr/share/texmf-texlive/tex/generic/hyphen/hyphen.tex)
(/usr/share/texmf-texlive/tex/generic/hyphen/ushyphmax.tex)
(/usr/share/texmf-texlive/tex/generic/hyphen/dumyhyph.tex)
(/usr/share/texmf-texlive/tex/generic/hyphen/zerohyph.tex))
=================================
Applying patch file ltpatch.ltx
=================================

...back 1 page
                                                  
LaTeX2e <2003/12/01>
hacks, control, par, spacing, files, font encodings, lengths,
====================================

Local config file fonttext.cfg used

====================================
(/usr/share/texmf-texlive/tex/latex/base/fonttext.cfg
(/usr/share/texmf/tex/latex/base/fonttext.ltx
=== Don't modify this file, use a .cfg file instead ===

(/usr/share/texmf/tex/latex/base/omlenc.def)
(/usr/share/texmf/tex/latex/base/t1enc.def)
(/usr/share/texmf/tex/latex/base/ot1enc.def)
(/usr/share/texmf/tex/latex/base/omsenc.def)
(/usr/share/texmf/tex/latex/base/t1cmr.fd)
(/usr/share/texmf/tex/latex/base/ot1cmr.fd)
(/usr/share/texmf/tex/latex/base/ot1cmss.fd)
(/usr/share/texmf/tex/latex/base/ot1cmtt.fd)))
====================================

Local config file fontmath.cfg used

====================================
(/usr/share/texmf-texlive/tex/latex/base/fontmath.cfg
(/usr/share/texmf/tex/latex/base/fontmath.ltx
=== Don't modify this file, use a .cfg file instead ===

(/usr/share/texmf/tex/latex/base/omlcmm.fd)
(/usr/share/texmf/tex/latex/base/omscmsy.fd)
(/usr/share/texmf/tex/latex/base/omxcmex.fd)
(/usr/share/texmf/tex/latex/base/ucmr.fd)))
====================================

Local config file preload.cfg used

=====================================
(/usr/share/texmf-texlive/tex/latex/base/preload.cfg
(/usr/share/texmf/tex/latex/base/preload.ltx)) page nos., x-ref, environments,
center, verbatim, math definitions, boxes, title, sectioning, contents,
floats, footnotes, index, bibliography, output,
===========================================
Local configuration file hyphen.cfg used
===========================================
(/usr/share/texmf-texlive/tex/generic/babel/hyphen.cfg
(/usr/share/texmf-texlive/tex/generic/hyphen/hyphen.tex)
(/usr/share/texmf-texlive/tex/generic/hyphen/ushyphmax.tex)
(/usr/share/texmf-texlive/tex/generic/hyphen/dumyhyph.tex)
(/usr/share/texmf-texlive/tex/generic/hyphen/zerohyph.tex))
=================================
Applying patch file ltpatch.ltx
=================================
(/usr/share/texmf/tex/latex/base/ltpatch.ltx)
 ) )
Beginning to dump on file latex.fmt
 (format=latex 2016.7.28)
4927 strings of total length 66989
44190 memory locations dumped; current usage is 144&42202
3270 multiletter control sequences
\font\nullfont=nullfont
\font\OMX/cmex/m/n/10=cmex10
\font\tenln=line10
\font\tenlnw=linew10
\font\tencirc=lcircle10
\font\tencircw=lcirclew10
\font\OT1/cmr/m/n/5=cmr5
\font\OT1/cmr/m/n/7=cmr7
\font\OT1/cmr/m/n/10=cmr10
\font\OML/cmm/m/it/5=cmmi5
\font\OML/cmm/m/it/7=cmmi7
\font\OML/cmm/m/it/10=cmmi10
\font\OMS/cmsy/m/n/5=cmsy5
\font\OMS/cmsy/m/n/7=cmsy7
\font\OMS/cmsy/m/n/10=cmsy10
3633 words of font info for 14 preloaded fonts
28 hyphenation exceptions
Hyphenation trie of length 9934 has 560 ops out of 35111
  2 for language 2
  377 for language 1
  181 for language 0
0 words of pdfTeX memory
0 indirect objects
No pages of output.
Transcript written on latex.log.

```

Any help is highly appreciated!

---

### Post by QDR06VV9 on 2016-07-28
Have a look here: [http://askubuntu.com/questions/163682/how-do-i-install-the-latest-tex-live-2012](http://askubuntu.com/questions/163682/how-do-i-install-the-latest-tex-live-2012)

---

### Post by neunlemminge on 2016-07-28
> **runrickus said:**
> Have a look here: [http://askubuntu.com/questions/163682/how-do-i-install-the-latest-tex-live-2012](http://askubuntu.com/questions/163682/how-do-i-install-the-latest-tex-live-2012)

I did as described there:
sudo add-apt-repository ppa:texlive-backports/ppa
sudo apt-get update
sudo apt-get install texlive

but still get the issue with fmtutil-sys:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  latex-beamer latex-xcolor pgf prosper tex-gyre texlive-extra-utils
  texlive-font-utils texlive-fonts-recommended texlive-fonts-recommended-doc
  texlive-generic-recommended texlive-latex-recommended
  texlive-latex-recommended-doc texlive-pstricks texlive-pstricks-doc tipa
  ttf-marvosym
Suggested packages:
  texlive-doc-en purifyeps chktex latexmk dvipng xindy dvidvi fragmaster
  latexdiff
The following NEW packages will be installed:
  latex-beamer latex-xcolor pgf prosper tex-gyre texlive texlive-extra-utils
  texlive-font-utils texlive-fonts-recommended texlive-fonts-recommended-doc
  texlive-generic-recommended texlive-latex-recommended
  texlive-latex-recommended-doc texlive-pstricks texlive-pstricks-doc tipa
  ttf-marvosym
0 upgraded, 17 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 181 MB of archives.
After this operation, 268 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://cz.archive.ubuntu.com/ubuntu/ precise/main latex-xcolor all 2.11-1 [609 kB]
Get:2 http://ppa.launchpad.net/texlive-backports/ppa/ubuntu/ precise/main tex-gyre all 2.004.1-4~precise1 [16.1 MB]
Get:3 http://cz.archive.ubuntu.com/ubuntu/ precise/main pgf all 2.10-1 [5,668 kB]
Get:4 http://cz.archive.ubuntu.com/ubuntu/ precise/main latex-beamer all 3.10-1 [2,559 kB]
Get:5 http://cz.archive.ubuntu.com/ubuntu/ precise/main prosper all 1.00.4+cvs.2007.05.01-4 [449 kB]
Get:6 http://cz.archive.ubuntu.com/ubuntu/ precise/universe ttf-marvosym all 0.1+dfsg-2 [46.9 kB]
Get:7 http://ppa.launchpad.net/texlive-backports/ppa/ubuntu/ precise/main texlive-latex-recommended all 2012.20120611-3~ubuntu12.04.1 [6,784 kB]
Get:8 http://ppa.launchpad.net/texlive-backports/ppa/ubuntu/ precise/main texlive-generic-recommended all 2012.20120611-3~ubuntu12.04.1 [2,141 kB]
Get:9 http://ppa.launchpad.net/texlive-backports/ppa/ubuntu/ precise/main texlive-pstricks all 2012.20120611-1~ubuntu12.04.1 [25.5 MB]
Get:10 http://ppa.launchpad.net/texlive-backports/ppa/ubuntu/ precise/main texlive-fonts-recommended all 2012.20120611-3~ubuntu12.04.1 [5,483 kB]
Get:11 http://ppa.launchpad.net/texlive-backports/ppa/ubuntu/ precise/main texlive all 2012.20120611-3~ubuntu12.04.1 [36.8 kB]
Get:12 http://ppa.launchpad.net/texlive-backports/ppa/ubuntu/ precise/main texlive-extra-utils all 2012.20120611-1~ubuntu12.04.1 [2,549 kB]
Get:13 http://ppa.launchpad.net/texlive-backports/ppa/ubuntu/ precise/main texlive-font-utils all 2012.20120611-1~ubuntu12.04.1 [1,698 kB]
Get:14 http://ppa.launchpad.net/texlive-backports/ppa/ubuntu/ precise/main texlive-fonts-recommended-doc all 2012.20120611-3~ubuntu12.04.1 [3,914 kB]
Get:15 http://ppa.launchpad.net/texlive-backports/ppa/ubuntu/ precise/main texlive-latex-recommended-doc all 2012.20120611-3~ubuntu12.04.1 [34.7 MB]
Get:16 http://ppa.launchpad.net/texlive-backports/ppa/ubuntu/ precise/main texlive-pstricks-doc all 2012.20120611-1~ubuntu12.04.1 [69.9 MB]
Get:17 http://ppa.launchpad.net/texlive-backports/ppa/ubuntu/ precise/main tipa all 2:1.3-17~precise1 [3,323 kB]
Fetched 181 MB in 1min 54s (1,589 kB/s)                                        
Selecting previously unselected package tex-gyre.
(Reading database ... 1730331 files and directories currently installed.)
Unpacking tex-gyre (from .../tex-gyre_2.004.1-4~precise1_all.deb) ...
Selecting previously unselected package texlive-latex-recommended.
Unpacking texlive-latex-recommended (from .../texlive-latex-recommended_2012.20120611-3~ubuntu12.04.1_all.deb) ...
Selecting previously unselected package latex-xcolor.
Unpacking latex-xcolor (from .../latex-xcolor_2.11-1_all.deb) ...
Selecting previously unselected package pgf.
Unpacking pgf (from .../archives/pgf_2.10-1_all.deb) ...
Selecting previously unselected package latex-beamer.
Unpacking latex-beamer (from .../latex-beamer_3.10-1_all.deb) ...
Selecting previously unselected package texlive-generic-recommended.
Unpacking texlive-generic-recommended (from .../texlive-generic-recommended_2012.20120611-3~ubuntu12.04.1_all.deb) ...
Selecting previously unselected package texlive-pstricks.
Unpacking texlive-pstricks (from .../texlive-pstricks_2012.20120611-1~ubuntu12.04.1_all.deb) ...
Selecting previously unselected package prosper.
Unpacking prosper (from .../prosper_1.00.4+cvs.2007.05.01-4_all.deb) ...
Selecting previously unselected package ttf-marvosym.
Unpacking ttf-marvosym (from .../ttf-marvosym_0.1+dfsg-2_all.deb) ...
Selecting previously unselected package texlive-fonts-recommended.
Unpacking texlive-fonts-recommended (from .../texlive-fonts-recommended_2012.20120611-3~ubuntu12.04.1_all.deb) ...
Selecting previously unselected package texlive.
Unpacking texlive (from .../texlive_2012.20120611-3~ubuntu12.04.1_all.deb) ...
Selecting previously unselected package texlive-extra-utils.
Unpacking texlive-extra-utils (from .../texlive-extra-utils_2012.20120611-1~ubuntu12.04.1_all.deb) ...
Selecting previously unselected package texlive-font-utils.
Unpacking texlive-font-utils (from .../texlive-font-utils_2012.20120611-1~ubuntu12.04.1_all.deb) ...
Selecting previously unselected package texlive-fonts-recommended-doc.
Unpacking texlive-fonts-recommended-doc (from .../texlive-fonts-recommended-doc_2012.20120611-3~ubuntu12.04.1_all.deb) ...
Selecting previously unselected package texlive-latex-recommended-doc.
Unpacking texlive-latex-recommended-doc (from .../texlive-latex-recommended-doc_2012.20120611-3~ubuntu12.04.1_all.deb) ...
Selecting previously unselected package texlive-pstricks-doc.
Unpacking texlive-pstricks-doc (from .../texlive-pstricks-doc_2012.20120611-1~ubuntu12.04.1_all.deb) ...
Selecting previously unselected package tipa.
Unpacking tipa (from .../tipa_2%3a1.3-17~precise1_all.deb) ...
Processing triggers for fontconfig ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 3 added doc-base files...
Registering documents with scrollkeeper...
Processing triggers for install-info ...
Setting up texlive-latex-base (2012.20120611-3~ubuntu12.04.1) ...
Running mktexlsr. This may take some time... done.
Building format(s) --all --cnffile /etc/texmf/fmt.d/10texlive-latex-base.cnf.
    This may take some time... 
fmtutil-sys failed. Output has been stored in
/tmp/fmtutil.sFoWXJsK
Please include this file if you report a bug.

dpkg: error processing texlive-latex-base (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up tex-gyre (2.004.1-4~precise1) ...
Installing new version of config file /etc/X11/fonts/Type1/tex-gyre.scale ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    No apport report written because MaxReports is reached already
                                  No apport report written because MaxReports is reached already
                dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on texlive-latex-base (>= 2012.20120516); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-xcolor:
 latex-xcolor depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing latex-xcolor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pgf:
 pgf depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
 pgf depends on latex-xcolor (>= 2.00-1); however:
  Package latex-xcolor is not configured yet.
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
Setting up texlive-generic-recommended (2012.20120611-3~ubuntu12.04.1) ...
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of prosper:
 prosper depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 prosper depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing prosper (--configure):
 dependency problems - leaving unconfigured
Setting up ttf-marvosym (0.1+dfsg-2) ...
Setting up texlive-fonts-recommended (2012.20120611-3~ubuntu12.04.1) ...
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of texlive:
 texlive depends on texlive-latex-base (>= 2012.20120516); however:
  Package texlive-latex-base is not configured yet.
 texlive depends on texlive-latex-recommended (>= 2012.20120516); however:
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing texlive (--configure):
 dependency problems - leaving unconfigured
Setting up texlive-extra-utils (2012.20120611-1~ubuntu12.04.1) ...
Setting up texlive-font-utils (2012.20120611-1~ubuntu12.04.1) ...
Setting up texlive-fonts-recommended-doc (2012.20120611-3~ubuntu12.04.1) ...
Setting up texlive-latex-recommended-doc (2012.20120611-3~ubuntu12.04.1) ...
Setting up texlive-pstricks-doc (2012.20120611-1~ubuntu12.04.1) ...
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of tipa:
 tipa depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing tipa (--configure):
 dependency problems - leaving unconfigured
Processing triggers for tex-common ...
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... done.
Running mktexlsr /var/lib/texmf ... done.
Setting up texlive-pstricks (2012.20120611-1~ubuntu12.04.1) ...
Processing triggers for tex-common ...
Running mktexlsr. This may take some time... done.
Errors were encountered while processing:
 texlive-latex-base
 texlive-latex-recommended
 latex-xcolor
 pgf
 latex-beamer
 prosper
 texlive
 tipa
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
/tmp/fmtutil.sFoWXJsK reads
```
fmtutil: running `luatex -ini   -jobname=dvilualatex -progname=dvilualatex dvilu
alatex.ini' ...
This is LuaTeX, Version beta-0.70.1-2011120612  (INITEX)
 restricted \write18 enabled.
(/usr/share/texlive/texmf-dist/tex/latex/latexconfig/dvilualatex.ini
(/usr/share/texlive/texmf-dist/tex/latex/latexconfig/lualatexiniconfig.tex)
(/usr/share/texlive/texmf/tex/generic/config/pdftexconfig.tex
(/var/lib/texmf/tex/generic/config/pdftexconfig-paper.tex))
(/usr/share/texmf/tex/latex/base/latex.ltx
(/usr/share/texmf/tex/latex/base/texsys.cfg)
./texsys.aux found


\@currdir set to: ./.


Assuming \openin and \input 
have the same search path.


Defining UNIX/DOS style filename parser.

catcodes, registers, compatibility for TeX 2,  parameters,

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
! You are attempting to make a LaTeX format from a source file
! That is more than five years old.
!
! If you enter <return> to scroll past this message then the format
! will be built, but please consider obtaining newer source files
! before continuing to build LaTeX.
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

! LaTeX source files more than 5 years old!.
l.540 ...aTeX source files more than 5 years old!}
                                                  
LaTeX2e <2003/12/01>
hacks, control, par, spacing, files, font encodings, lengths,
====================================

Local config file fonttext.cfg used

====================================
(/usr/share/texlive/texmf-dist/tex/latex/base/fonttext.cfg
(/usr/share/texmf/tex/latex/base/fonttext.ltx
=== Don't modify this file, use a .cfg file instead ===

(/usr/share/texmf/tex/latex/base/omlenc.def)
(/usr/share/texmf/tex/latex/base/t1enc.def)
(/usr/share/texmf/tex/latex/base/ot1enc.def)
(/usr/share/texmf/tex/latex/base/omsenc.def)
(/usr/share/texmf/tex/latex/base/t1cmr.fd)
(/usr/share/texmf/tex/latex/base/ot1cmr.fd)
(/usr/share/texmf/tex/latex/base/ot1cmss.fd)
(/usr/share/texmf/tex/latex/base/ot1cmtt.fd)))
====================================

Local config file fontmath.cfg used

====================================
(/usr/share/texlive/texmf-dist/tex/latex/base/fontmath.cfg
(/usr/share/texmf/tex/latex/base/fontmath.ltx
=== Don't modify this file, use a .cfg file instead ===

(/usr/share/texmf/tex/latex/base/omlcmm.fd)
(/usr/share/texmf/tex/latex/base/omscmsy.fd)
(/usr/share/texmf/tex/latex/base/omxcmex.fd)
(/usr/share/texmf/tex/latex/base/ucmr.fd)))
====================================

Local config file preload.cfg used

=====================================
(/usr/share/texlive/texmf-dist/tex/latex/base/preload.cfg
(/usr/share/texmf/tex/latex/base/preload.ltx)) page nos., x-ref, environments,
center, verbatim, math definitions, boxes, title, sectioning, contents,
floats, footnotes, index, bibliography, output,
===========================================
Local configuration file hyphen.cfg used
===========================================
(/usr/share/texlive/texmf-dist/tex/luatex/hyph-utf8/hyphen.cfg
(/usr/share/texlive/texmf/tex/generic/hyphen/hyphen.tex)
(/usr/share/texlive/texmf/tex/generic/hyphen/dumyhyph.tex)
(/usr/share/texlive/texmf/tex/generic/hyphen/zerohyph.tex))
=================================
Applying patch file ltpatch.ltx
=================================
(/usr/share/texmf/tex/latex/base/ltpatch.ltx)
)
(/usr/share/texlive/texmf-dist/tex/latex/latexconfig/lualatex-patch-kernel.tex)
(/usr/share/texlive/texmf-dist/tex/latex/latexconfig/lualatexquotejobname.tex)
(/usr/share/texlive/texmf-dist/tex/latex/latexconfig/lualatex-reset-codes.tex)
(/usr/share/texlive/texmf/tex/generic/config/luatex-unicode-letters.tex
loading Unicode properties) )
Beginning to dump on file dvilualatex.fmt
 (format=dvilualatex 2016.7.29)
4891 strings using 33076 bytes
151009 memory locations dumped; current usage is 124&46629
3545 multiletter control sequences
\font\nullfont=nullfont
\font\OMX/cmex/m/n/10=cmex10
\font\tenln=line10
\font\tenlnw=linew10
\font\tencirc=lcircle10
\font\tencircw=lcirclew10
\font\OT1/cmr/m/n/5=cmr5
\font\OT1/cmr/m/n/7=cmr7
\font\OT1/cmr/m/n/10=cmr10
\font\OML/cmm/m/it/5=cmmi5
\font\OML/cmm/m/it/7=cmmi7
\font\OML/cmm/m/it/10=cmmi10
\font\OMS/cmsy/m/n/5=cmsy5
\font\OMS/cmsy/m/n/7=cmsy7
\font\OMS/cmsy/m/n/10=cmsy10
14 preloaded fonts
0 words of pdf memory
0 indirect objects
No pages of output.
Transcript written on dvilualatex.log.

```

---

### Post by QDR06VV9 on 2016-07-28
Yuck!...This may be over my pay grade:)
What dose this do:
```
sudo apt-get install texlive-full
```
EDIT Time got away from me I have to get ready and go to work now..will check back in the morning.

---

### Post by neunlemminge on 2016-07-29
similiar issue...

fmtutil still fails (3 times), e.g.:

```
Building format(s) --byengine luatex.
    This may take some time... 
fmtutil-sys failed. Output has been stored in
/tmp/fmtutil.RxDwjBEt
Please include this file if you report a bug.

```

with fmtutil.RxDwjBEt

```
fmtutil: running `luatex -ini   -jobname=luatex -progname=luatex luatex.ini' ...
This is LuaTeX, Version beta-0.70.2-2012062323 (TeX Live 2012/Debian) (INITEX)
 restricted \write18 enabled.
(/usr/share/texlive/texmf-dist/tex/plain/config/luatex.ini
(/usr/share/texlive/texmf/tex/generic/config/luatexiniconfig.tex)
(/usr/share/texlive/texmf/tex/generic/config/luatex-unicode-letters.tex
loading Unicode properties)
(/usr/share/texlive/texmf-dist/tex/plain/config/pdfetex.ini
(/usr/share/texlive/texmf/tex/generic/config/pdftexconfig.tex
(/var/lib/texmf/tex/generic/config/pdftexconfig-paper.tex))
(/usr/share/texlive/texmf-dist/tex/luatex/hyph-utf8/etex.src
(/usr/share/texlive/texmf-dist/tex/plain/base/plain.tex
Preloading the plain format: codes, registers, parameters, fonts, more fonts,
macros, math definitions, output routines, hyphenation
(/usr/share/texlive/texmf/tex/generic/hyphen/hyphen.tex
[skipping from \patterns to end-of-file...]))
(/usr/share/texlive/texmf-dist/tex/plain/etex/etexdefs.lib
Skipping module "grouptypes"; Loading module "interactionmodes";
Skipping module "nodetypes"; Skipping module "iftypes";)
(/var/lib/texmf/tex/generic/config/language.def
(/usr/share/texlive/texmf/tex/generic/hyphen/hyphen.tex))
Augmenting the Plain TeX definitions: \tracingall;
Adding new e-TeX definitions: \eTeX, \loggingall, \tracingnone,
register allocation; extended register allocation; 
Recycling: \addlanguage, \@nswer (not defined), \@sk, \b@dresponsetrue,
\b@dresponsefalse, \ch@ckforyn, \mayber@cycle, \et@xabort, \et@xbuf,
\et@xfmtsrc, \et@xfilehdr, \et@xinf, \et@xpatterns, \l@ngdefnfile, \n@xt,
\p@rse (not defined), \pr@mpt (not defined), \pr@mptloop (not defined),
\forcer@cycle, \usef@llback, \usef@llbacktrue, \usef@llbackfalse, 
Retaining: \et@xerr, \et@xinput, \et@xlibhdr, \et@xmsg, \et@xtoks, \et@xwarn,
\et@xl@@d, \et@xl@ad, \et@xload, \et@xlang, \et@xhash, \eTeX, \etexhdrchk,
\etexstatus, \module, \uselanguage, \r@tain, \r@cycle,)
(/usr/share/texlive/texmf-dist/tex/plain/config/pdftexmagfix.tex) ) )
Beginning to dump on file luatex.fmt
 (format=luatex 2016.7.29)
3181 strings using 9736 bytes
69031 memory locations dumped; current usage is 103&7787
1737 multiletter control sequences
\font\nullfont=nullfont
\font\tenrm=cmr10
\font\preloaded=cmr9
\font\preloaded=cmr8
\font\sevenrm=cmr7
\font\preloaded=cmr6
\font\fiverm=cmr5
\font\teni=cmmi10
\font\preloaded=cmmi9
\font\preloaded=cmmi8
\font\seveni=cmmi7
\font\preloaded=cmmi6
\font\fivei=cmmi5
\font\tensy=cmsy10
\font\preloaded=cmsy9
\font\preloaded=cmsy8
\font\sevensy=cmsy7
\font\preloaded=cmsy6
\font\fivesy=cmsy5
\font\tenex=cmex10
\font\preloaded=cmss10
\font\preloaded=cmssq8
\font\preloaded=cmssi10
\font\preloaded=cmssqi8
\font\tenbf=cmbx10
\font\preloaded=cmbx9
\font\preloaded=cmbx8
\font\sevenbf=cmbx7
\font\preloaded=cmbx6
\font\fivebf=cmbx5
\font\tentt=cmtt10
\font\preloaded=cmtt9
\font\preloaded=cmtt8
\font\preloaded=cmsltt10
\font\tensl=cmsl10
\font\preloaded=cmsl9
\font\preloaded=cmsl8
\font\tenit=cmti10
\font\preloaded=cmti9
\font\preloaded=cmti8
\font\preloaded=cmti7
\font\preloaded=cmu10
\font\preloaded=cmmib10
\font\preloaded=cmbsy10
\font\preloaded=cmcsc10
\font\preloaded=cmssbx10
\font\preloaded=cmdunh10
\font\preloaded=cmr7 at 14.51799pt
\font\preloaded=cmtt10 at 14.4pt
\font\preloaded=cmssbx10 at 14.4pt
\font\preloaded=manfnt
50 preloaded fonts
0 words of pdf memory
0 indirect objects
No pages of output.
Transcript written on luatex.log.
fmtutil: /var/lib/texmf/web2c/luatex/luatex.fmt installed.
fmtutil: running `luatex -ini   -jobname=dviluatex -progname=dviluatex dviluatex
.ini' ...
This is LuaTeX, Version beta-0.70.2-2012062323 (TeX Live 2012/Debian) (INITEX)
 restricted \write18 enabled.
(/usr/share/texlive/texmf-dist/tex/plain/config/dviluatex.ini
(/usr/share/texlive/texmf/tex/generic/config/luatexiniconfig.tex)
(/usr/share/texlive/texmf/tex/generic/config/luatex-unicode-letters.tex
loading Unicode properties)
(/usr/share/texlive/texmf-dist/tex/plain/config/etex.ini
(/usr/share/texlive/texmf-dist/tex/luatex/hyph-utf8/etex.src
(/usr/share/texlive/texmf-dist/tex/plain/base/plain.tex
Preloading the plain format: codes, registers, parameters, fonts, more fonts,
macros, math definitions, output routines, hyphenation
(/usr/share/texlive/texmf/tex/generic/hyphen/hyphen.tex
[skipping from \patterns to end-of-file...]))
(/usr/share/texlive/texmf-dist/tex/plain/etex/etexdefs.lib
Skipping module "grouptypes"; Loading module "interactionmodes";
Skipping module "nodetypes"; Skipping module "iftypes";)
(/var/lib/texmf/tex/generic/config/language.def
(/usr/share/texlive/texmf/tex/generic/hyphen/hyphen.tex))
Augmenting the Plain TeX definitions: \tracingall;
Adding new e-TeX definitions: \eTeX, \loggingall, \tracingnone,
register allocation; extended register allocation; 
Recycling: \addlanguage, \@nswer (not defined), \@sk, \b@dresponsetrue,
\b@dresponsefalse, \ch@ckforyn, \mayber@cycle, \et@xabort, \et@xbuf,
\et@xfmtsrc, \et@xfilehdr, \et@xinf, \et@xpatterns, \l@ngdefnfile, \n@xt,
\p@rse (not defined), \pr@mpt (not defined), \pr@mptloop (not defined),
\forcer@cycle, \usef@llback, \usef@llbacktrue, \usef@llbackfalse, 
Retaining: \et@xerr, \et@xinput, \et@xlibhdr, \et@xmsg, \et@xtoks, \et@xwarn,
\et@xl@@d, \et@xl@ad, \et@xload, \et@xlang, \et@xhash, \eTeX, \etexhdrchk,
\etexstatus, \module, \uselanguage, \r@tain, \r@cycle,) ) )
Beginning to dump on file dviluatex.fmt
 (format=dviluatex 2016.7.29)
3164 strings using 9659 bytes
69031 memory locations dumped; current usage is 103&7756
1735 multiletter control sequences
\font\nullfont=nullfont
\font\tenrm=cmr10
\font\preloaded=cmr9
\font\preloaded=cmr8
\font\sevenrm=cmr7
\font\preloaded=cmr6
\font\fiverm=cmr5
\font\teni=cmmi10
\font\preloaded=cmmi9
\font\preloaded=cmmi8
\font\seveni=cmmi7
\font\preloaded=cmmi6
\font\fivei=cmmi5
\font\tensy=cmsy10
\font\preloaded=cmsy9
\font\preloaded=cmsy8
\font\sevensy=cmsy7
\font\preloaded=cmsy6
\font\fivesy=cmsy5
\font\tenex=cmex10
\font\preloaded=cmss10
\font\preloaded=cmssq8
\font\preloaded=cmssi10
\font\preloaded=cmssqi8
\font\tenbf=cmbx10
\font\preloaded=cmbx9
\font\preloaded=cmbx8
\font\sevenbf=cmbx7
\font\preloaded=cmbx6
\font\fivebf=cmbx5
\font\tentt=cmtt10
\font\preloaded=cmtt9
\font\preloaded=cmtt8
\font\preloaded=cmsltt10
\font\tensl=cmsl10
\font\preloaded=cmsl9
\font\preloaded=cmsl8
\font\tenit=cmti10
\font\preloaded=cmti9
\font\preloaded=cmti8
\font\preloaded=cmti7
\font\preloaded=cmu10
\font\preloaded=cmmib10
\font\preloaded=cmbsy10
\font\preloaded=cmcsc10
\font\preloaded=cmssbx10
\font\preloaded=cmdunh10
\font\preloaded=cmr7 at 14.51799pt
\font\preloaded=cmtt10 at 14.4pt
\font\preloaded=cmssbx10 at 14.4pt
\font\preloaded=manfnt
50 preloaded fonts
0 words of pdf memory
0 indirect objects
No pages of output.
Transcript written on dviluatex.log.
fmtutil: /var/lib/texmf/web2c/luatex/dviluatex.fmt installed.
fmtutil: running `luatex -ini   -jobname=dvilualatex -progname=dvilualatex dvilu
alatex.ini' ...
This is LuaTeX, Version beta-0.70.2-2012062323 (TeX Live 2012/Debian) (INITEX)
 restricted \write18 enabled.
(/usr/share/texlive/texmf-dist/tex/latex/latexconfig/dvilualatex.ini
(/usr/share/texlive/texmf-dist/tex/latex/latexconfig/lualatexiniconfig.tex)
(/usr/share/texlive/texmf/tex/generic/config/pdftexconfig.tex
(/var/lib/texmf/tex/generic/config/pdftexconfig-paper.tex))
(/usr/share/texmf/tex/latex/base/latex.ltx
(/usr/share/texmf/tex/latex/base/texsys.cfg)
./texsys.aux found


\@currdir set to: ./.


Assuming \openin and \input 
have the same search path.


Defining UNIX/DOS style filename parser.

catcodes, registers, compatibility for TeX 2,  parameters,

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
! You are attempting to make a LaTeX format from a source file
! That is more than five years old.
!
! If you enter <return> to scroll past this message then the format
! will be built, but please consider obtaining newer source files
! before continuing to build LaTeX.
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

! LaTeX source files more than 5 years old!.
l.540 ...aTeX source files more than 5 years old!}
                                                  
LaTeX2e <2003/12/01>
hacks, control, par, spacing, files, font encodings, lengths,
====================================

Local config file fonttext.cfg used

====================================
(/usr/share/texlive/texmf-dist/tex/latex/base/fonttext.cfg
(/usr/share/texmf/tex/latex/base/fonttext.ltx
=== Don't modify this file, use a .cfg file instead ===

(/usr/share/texmf/tex/latex/base/omlenc.def)
(/usr/share/texmf/tex/latex/base/t1enc.def)
(/usr/share/texmf/tex/latex/base/ot1enc.def)
(/usr/share/texmf/tex/latex/base/omsenc.def)
(/usr/share/texmf/tex/latex/base/t1cmr.fd)
(/usr/share/texmf/tex/latex/base/ot1cmr.fd)
(/usr/share/texmf/tex/latex/base/ot1cmss.fd)
(/usr/share/texmf/tex/latex/base/ot1cmtt.fd)))
====================================

Local config file fontmath.cfg used

====================================
(/usr/share/texlive/texmf-dist/tex/latex/base/fontmath.cfg
(/usr/share/texmf/tex/latex/base/fontmath.ltx
=== Don't modify this file, use a .cfg file instead ===

(/usr/share/texmf/tex/latex/base/omlcmm.fd)
(/usr/share/texmf/tex/latex/base/omscmsy.fd)
(/usr/share/texmf/tex/latex/base/omxcmex.fd)
(/usr/share/texmf/tex/latex/base/ucmr.fd)))
====================================

Local config file preload.cfg used

=====================================
(/usr/share/texlive/texmf-dist/tex/latex/base/preload.cfg
(/usr/share/texmf/tex/latex/base/preload.ltx)) page nos., x-ref, environments,
center, verbatim, math definitions, boxes, title, sectioning, contents,
floats, footnotes, index, bibliography, output,
===========================================
Local configuration file hyphen.cfg used
===========================================
(/usr/share/texlive/texmf-dist/tex/luatex/hyph-utf8/hyphen.cfg
(/usr/share/texlive/texmf/tex/generic/hyphen/hyphen.tex)
(/usr/share/texlive/texmf/tex/generic/hyphen/dumyhyph.tex)
(/usr/share/texlive/texmf/tex/generic/hyphen/zerohyph.tex))
=================================
Applying patch file ltpatch.ltx
=================================
(/usr/share/texmf/tex/latex/base/ltpatch.ltx)
)
(/usr/share/texlive/texmf-dist/tex/latex/latexconfig/lualatex-patch-kernel.tex)
(/usr/share/texlive/texmf-dist/tex/latex/latexconfig/lualatexquotejobname.tex)
(/usr/share/texlive/texmf-dist/tex/latex/latexconfig/lualatex-reset-codes.tex)
(/usr/share/texlive/texmf/tex/generic/config/luatex-unicode-letters.tex
loading Unicode properties) )
Beginning to dump on file dvilualatex.fmt
 (format=dvilualatex 2016.7.29)
4894 strings using 33082 bytes
151009 memory locations dumped; current usage is 124&46629
3546 multiletter control sequences
\font\nullfont=nullfont
\font\OMX/cmex/m/n/10=cmex10
\font\tenln=line10
\font\tenlnw=linew10
\font\tencirc=lcircle10
\font\tencircw=lcirclew10
\font\OT1/cmr/m/n/5=cmr5
\font\OT1/cmr/m/n/7=cmr7
\font\OT1/cmr/m/n/10=cmr10
\font\OML/cmm/m/it/5=cmmi5
\font\OML/cmm/m/it/7=cmmi7
\font\OML/cmm/m/it/10=cmmi10
\font\OMS/cmsy/m/n/5=cmsy5
\font\OMS/cmsy/m/n/7=cmsy7
\font\OMS/cmsy/m/n/10=cmsy10
14 preloaded fonts
0 words of pdf memory
0 indirect objects
No pages of output.
Transcript written on dvilualatex.log.

```

any ideas are highly appreciated... Unfortunatly, this is above my knowledge.


> **runrickus said:**
> Yuck!...This may be over my pay grade:)
What dose this do:
```
sudo apt-get install texlive-full
```
EDIT Time got away from me I have to get ready and go to work now..will check back in the morning.

---

### Post by QDR06VV9 on 2016-07-29
The Below is an indication of something in the process is corrupt
```
Beginning to dump on file dvilualatex.fmt  (format=dvilualatex 2016.7.29) 4894 strings using 33082 bytes 151009 memory locations dumped; current usage is 124&46629
```
And what that may be, is just above my skill set. If it were me I would take the information you have here to their forums: [http://latex-community.org/forum/viewforum.php?f=12](http://latex-community.org/forum/viewforum.php?f=12)
And see if they can help you sort this out.
Very Sorry I could not be of further use to you.
Kind Regards

---

### Post by neunlemminge on 2016-07-29
Thank you for your help. Something seems to be severely messed up. I tried removing and re-installing tex-common and texlive, even upgraded to 14.04, but still to not get latex to run. Looks as if I have to switch over to Windows :(

> **runrickus said:**
> The Below is an indication of something in the process is corrupt
```
Beginning to dump on file dvilualatex.fmt  (format=dvilualatex 2016.7.29) 4894 strings using 33082 bytes 151009 memory locations dumped; current usage is 124&46629
```
And what that may be, is just above my skill set. If it were me I would take the information you have here to their forums: [http://latex-community.org/forum/viewforum.php?f=12](http://latex-community.org/forum/viewforum.php?f=12)
And see if they can help you sort this out.
Very Sorry I could not be of further use to you.
Kind Regards

---

