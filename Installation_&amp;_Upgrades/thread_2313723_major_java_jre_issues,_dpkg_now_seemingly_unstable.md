---
title: "major java jre issues, dpkg now seemingly unstable"
date: 2016-02-15
forum: Installation &amp; Upgrades
---

### Post by rsleventhal2 on 2016-02-15
Hello all,

While trying to purge Oracle JRE and and reinstall the default JRE I managed to get my machine into a state where I need assistance.

Here's what I'm seeing in terminal:

```
#sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  jre1.8.0-73
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 126 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 415941 files and directories currently installed.)
Removing jre1.8.0-73 (1.8.073-1) ...
/var/lib/dpkg/info/jre1.8.0-73.postrm: line 586: /usr/sbin/alternatives: No such file or directory
dpkg: error processing package jre1.8.0-73 (--remove):
 subprocess installed post-removal script returned error exit status 127
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Any suggestions would be greatly appreciated as I use jEdit for PHP projects and, of course, that means that having a working JRE is essential.

TIA,
-Ray

SOLVED - Little did I know that the previous user of this system installed this JRE from an RPM file which he'd run 'alien' on.  Hence, the postrm script was RPM based.  I removed it and all is well

---

