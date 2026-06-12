---
title: "texlive again"
date: 2012-02-13
forum: Installation &amp; Upgrades
---

### Post by emamm2008 on 2012-02-13
Hello

In a recent upgrade to oneiric, texlive failed to upgrade.  I have tried remove --purge and install many times but the error persists (see below).

armagedon:~/Downloads$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  texlive-base texlive-binaries texlive-common texlive-doc-base texlive-latex-base texlive-latex-base-doc
The following NEW packages will be installed:
  texlive-base texlive-binaries texlive-common texlive-doc-base texlive-latex-base texlive-latex-base-doc
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/66.0 MB of archives.
After this operation, 127 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Preconfiguring packages ...
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 72213 package 'virtualbox-3.0':
 error in Version string '3.0.8-53138_Ubuntu_jaunty': invalid character in revision number
Selecting previously deselected package texlive-common.
(Reading database ... 391661 files and directories currently installed.)
Unpacking texlive-common (from .../texlive-common_2009-13_all.deb) ...
Selecting previously deselected package texlive-doc-base.
Unpacking texlive-doc-base (from .../texlive-doc-base_2009-2_all.deb) ...
Selecting previously deselected package texlive-binaries.
Unpacking texlive-binaries (from .../texlive-binaries_2009-11ubuntu1_amd64.deb) ...
Selecting previously deselected package texlive-base.
Unpacking texlive-base (from .../texlive-base_2009-13_all.deb) ...
Selecting previously deselected package texlive-latex-base.
Unpacking texlive-latex-base (from .../texlive-latex-base_2009-13_all.deb) ...
Selecting previously deselected package texlive-latex-base-doc.
Unpacking texlive-latex-base-doc (from .../texlive-latex-base-doc_2009-13_all.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Setting up texlive-common (2009-13) ...
Setting up texlive-doc-base (2009-2) ...
Setting up texlive-binaries (2009-11ubuntu1) ...
update-alternatives: using /usr/bin/xdvi-xaw to provide /usr/bin/xdvi.bin (xdvi.bin) in auto mode.
update-alternatives: using /usr/bin/bibtex.original to provide /usr/bin/bibtex (bibtex) in auto mode.
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVE... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.
Building format(s) --refresh.
        This may take some time... 
fmtutil-sys failed. Output has been stored in
/tmp/fmtutil.b6AJFJqD
Please include this file if you report a bug.

dpkg: error processing texlive-binaries (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-base:
 texlive-base depends on texlive-binaries (>= 2009-10); however:
  Package texlive-binaries is not configured yet.
dpkg: error processing texlive-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
 texlive-latex-base depends on texlive-binaries (>= 2009-1); however:
  Package texlive-binaries is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
Setting up texlive-latex-base-doc (2009-13) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                             Processing triggers for tex-common ...
Running mktexlsr. This may take some time... done.
Errors were encountered while processing:
 texlive-binaries
 texlive-base
 texlive-latex-base
E: Sub-process /usr/bin/dpkg returned an error code (1)


I have browsed the web for solutions but I could not find anything of help.

Many thanks

Ed

---

