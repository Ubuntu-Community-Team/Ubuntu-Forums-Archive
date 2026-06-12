---
title: "Problem installing tetex-bin"
date: 2006-08-13
forum: Installation &amp; Upgrades
---

### Post by asundaresan on 2006-08-13
Hi,

I recently upgraded from breezy to dapper and had problem with tetex. I uninstalled the tetex package.

```
apt-get remove --purge tetex-bin
```

And tried reinstalling it, but the problem persisted. Any suggestions or tips are welcome.

Aravind.

```

root@revathi:~# apt-get install tetex-bin
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  gs-gpl tetex-extra texinfo texi2html dvipng chktex lacheck rubber sam2p
Recommended packages:
  dialog psutils perl-tk libxml-parser-perl
The following NEW packages will be installed:
  tetex-bin
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/3388kB of archives.
After unpacking 7700kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package tetex-bin.
(Reading database ... 120426 files and directories currently installed.)
Unpacking tetex-bin (from .../tetex-bin_3.0-13ubuntu6_i386.deb) ...
Setting up tetex-bin (3.0-13ubuntu6) ...

Creating config file /etc/texmf/fmt.d/01tetex.cnf with new version
Running fmtutil-sys. This may take some time. ...
Error: `pdfetex -ini  -jobname=latex -progname=latex -translate-file=cp227.tcx *latex.ini' failed
Error: `pdfetex -ini  -jobname=pdflatex -progname=pdflatex -translate-file=cp227.tcx *pdflatex.ini' failed

###############################################################################
fmtutil: Error! Not all formats have been built successfully.
Visit the log files in directory
  /var/lib/texmf/web2c
for details.
###############################################################################

This is a summary of all `failed' messages and warnings:
`pdfetex -ini  -jobname=latex -progname=latex -translate-file=cp227.tcx *latex.ini' failed
`pdfetex -ini  -jobname=pdflatex -progname=pdflatex -translate-file=cp227.tcx *pdflatex.ini' failed

fmtutil failed. Output has been stored in
/tmp/tetex.postinst.XX6rqdTW
Please include this file if you report a bug.
dpkg: error processing tetex-bin (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 tetex-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@revathi:~#

```

---

### Post by asundaresan on 2006-08-14
I think the following might solve the problem. It did it for me.

```

apt-get remove --purge tex-common tetex-base tetex-extra tetex-bin latex-beamer lyx gnuhtml2latex latex2html latex2rtf

```

It may also be required to remove (with purge) any other packages that may be also removed as a result of the above action. Just do a quick check to see if any config files are left in /etc/texmf and also remove --purge any package that the file belongs to.

This can be done using ```
dpkg -S /path/to/file 
```.

Then on reinstalling all the removed packages there shouldn't be any problems.

---

