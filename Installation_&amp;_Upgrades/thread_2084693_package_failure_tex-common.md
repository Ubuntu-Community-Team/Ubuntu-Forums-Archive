---
title: "package failure: tex-common"
date: 2012-11-16
forum: Installation &amp; Upgrades
---

### Post by ganna10 on 2012-11-16
Hi,

I have been getting errors during updates all related to the tex-common package.  The main error is "package failure: tex-common 3.13~ubuntu 12.04.01".

When running
sudo apt-get update
sudo apt-get upgrade

I get
Errors were encountered while processing:
 tex-common
 texlive-luatex
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can anyone help with fixing this problem as I do need to use LateX?
Thanks,
Jane

---

### Post by raja.genupula on 2012-11-16
open your terminal and do these steps one by one 

```
dpkg -r tex-common
 dpkg -r texlive-luatex
sudo apt-get update
suso apt-get install -f
```

---

### Post by ganna10 on 2012-11-16
Thanks for the quick reply, I did as you mentioned and still having problems with tex-common.

Running dpkg for texlive-luatex, went smoothly but for tex-common I get this:

```
dpkg: dependency problems prevent removal of tex-common:
 lmodern depends on tex-common (>= 3).
 texlive-common depends on tex-common (>= 3).
 texlive-binaries depends on tex-common (>= 3).
 luatex depends on tex-common (>= 3.12).
 texlive-doc-base depends on tex-common (>= 3).
 texlive-base depends on tex-common (>= 3).
dpkg: error processing tex-common (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 tex-common

```

---

### Post by raja.genupula on 2012-11-16
open your terminal 

> sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get update
sudo apt-get install -f

then try again .

---

### Post by ganna10 on 2012-11-16
Still same problems:

```
Setting up tex-common (3.13~ubuntu12.04.1) ...
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... 
updmap-sys failed. Output has been stored in
/tmp/updmap.jtEJljTW
Please include this file if you report a bug.

Sometimes, not accepting conffile updates in /etc/texmf/updmap.d
causes updmap-sys to fail.  Please check for files with extension
.dpkg-dist or .ucf-dist in this directory

dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 tex-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

