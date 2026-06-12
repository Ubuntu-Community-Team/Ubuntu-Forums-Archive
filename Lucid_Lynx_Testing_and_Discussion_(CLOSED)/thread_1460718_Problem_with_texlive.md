---
title: "Problem with texlive"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gpan on 2010-04-23
I'm trying to install the following packages but I get the following errors. Can anyone help?

```
gpan@gpan-desktop:~$ sudo apt-get install tex-common texlive-binaries
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  debhelper
The following NEW packages will be installed:
  tex-common texlive-binaries
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 8,797kB of archives.
After this operation, 19.7MB of additional disk space will be used.
Get:1 http://ftp.ntua.gr/pub/linux/ubuntu/ lucid/main tex-common 2.06 [725kB]
Get:2 http://ftp.ntua.gr/pub/linux/ubuntu/ lucid/main texlive-binaries 2009-5 [8,073kB]
Fetched 8,797kB in 5s (1,484kB/s)           
Preconfiguring packages ...
Selecting previously deselected package tex-common.
(Reading database ... 
dpkg: warning: files list file for package `texinfo' missing, assuming package has no files currently installed.
(Reading database ... 245583 files and directories currently installed.)
Unpacking tex-common (from .../tex-common_2.06_all.deb) ...
Selecting previously deselected package texlive-binaries.
Unpacking texlive-binaries (from .../texlive-binaries_2009-5_amd64.deb) ...
Processing triggers for doc-base ...
Processing 2 changed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Setting up tex-common (2.06) ...
Error in /etc/texmf/texmf.d/55Fonts.cnf: TEXFONTMAPS not defined.
Error in /etc/texmf/texmf.cnf: TEXFONTMAPS not defined.
Error in /etc/texmf/texmf.d/05TeXMF.cnf: TEXMFMAIN not defined.
Error in /etc/texmf/texmf.cnf: TEXMFMAIN not defined.
Error in /etc/texmf/texmf.d/05TeXMF.cnf: TEXMFDIST not defined.
Error in /etc/texmf/texmf.cnf: TEXMFDIST not defined.
Error in /etc/texmf/texmf.d/05TeXMF.cnf: TEXMF not defined.
Error in /etc/texmf/texmf.cnf: TEXMF not defined.
Error in /etc/texmf/texmf.d/05TeXMF.cnf: TEXMF not defined.
Error in /etc/texmf/texmf.cnf: TEXMF not defined.
Error in /etc/texmf/texmf.d/05TeXMF.cnf: TEXMF not defined.
Error in /etc/texmf/texmf.cnf: TEXMF not defined.
Error in /etc/texmf/texmf.d/05TeXMF.cnf: TEXMF not defined.
Error in /etc/texmf/texmf.cnf: TEXMF not defined.
Unrecoverable errors in your configuration have been detected
in configuration files in /etc/texmf/.
If you've not seen debconf error messages,  see your mail for details
or use an interactive debconf frontend.

Exiting

dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-binaries:
 texlive-binaries depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-binaries (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 tex-common
 texlive-binaries
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

