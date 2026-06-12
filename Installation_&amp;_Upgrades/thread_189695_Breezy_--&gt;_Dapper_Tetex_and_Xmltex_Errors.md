---
title: "Breezy --&gt; Dapper: Tetex and Xmltex Errors"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by WoodyJI on 2006-06-05
I was upgrading from Breezy to Dapper and got errors installing tetex-base, tetex-bin, tetex-extra, and xmltex.  I tried to fix it using "sudo apt-get dist-update" but it didn't work.  The terminal spit out this message:
```
###############################################################################
fmtutil: Error! Not all formats have been built successfully.
Visit the log files in directory
  /var/lib/texmf/web2c
for details.
###############################################################################

This is a summary of all `failed' messages and warnings:
`etex -ini  -jobname=xmltex -progname=xmltex &latex xmltex.ini' failed

fmtutil failed. Output has been stored in
/tmp/tetex.postinst.XXMYi93r
Please include this file if you report a bug.
dpkg: error processing tetex-base (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of tetex-bin:
 tetex-bin depends on tetex-base (>= 3.0-4); however:
  Package tetex-base is not configured yet.
dpkg: error processing tetex-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tetex-extra:
 tetex-extra depends on tetex-base (>= 3.0-11); however:
  Package tetex-base is not configured yet.
 tetex-extra depends on tetex-bin (>= 2.99); however:
  Package tetex-bin is not configured yet.
dpkg: error processing tetex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xmltex:
 xmltex depends on tetex-base; however:
  Package tetex-base is not configured yet.
 xmltex depends on tetex-bin; however:
  Package tetex-bin is not configured yet.
 xmltex depends on tetex-extra; however:
  Package tetex-extra is not configured yet.
dpkg: error processing xmltex (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tetex-base
 tetex-bin
 tetex-extra
 xmltex
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Can anybody help me with this?

**EDIT** I was able to solve my own upgrade issues by using Symantic Package Manager to completely remove the TeX packages in question and then reinstall them successfully.  So, just for future reference...that's one way to solve the problem.

---

### Post by asundaresan on 2006-08-13
I'm also facing the same problem. However I'm not able to resolve it by uninstall and reinstall of the packages.

```
apt-get remove --purge tetex-bin tetex-extra
```

followed by 

```
apt-get install tetex-bin 
```

doesn't work for me. Any suggestions?

Aravind.

---

