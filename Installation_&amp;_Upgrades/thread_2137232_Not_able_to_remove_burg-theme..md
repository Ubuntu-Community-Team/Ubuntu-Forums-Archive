---
title: "Not able to remove burg-theme."
date: 2013-04-20
forum: Installation &amp; Upgrades
---

### Post by ssbijarnia on 2013-04-20
surendra@surendra-HP-Pavilion-dm4-Notebook-PC:~$ sudo apt-get purge burg-theme-cateyes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  burg-theme-cateyes burg-theme-what-am-i
0 upgraded, 0 newly installed, 2 to remove and 46 not upgraded.
2 not fully installed or removed.
After this operation, 6,201 kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: warning: files list file for package 'ubuntu-mono' missing; assuming package has no files currently installed
(Reading database ... 371021 files and directories currently installed.)
Removing burg-theme-cateyes ...
Generating burg.cfg ...
/usr/sbin/burg-probe: error: cannot stat `/boot/burg/locale'.
No path or device is specified.
Try `/usr/sbin/burg-probe --help' for more information.
dpkg: error processing burg-theme-cateyes (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing burg-theme-what-am-i ...
Generating burg.cfg ...
/usr/sbin/burg-probe: error: cannot stat `/boot/burg/locale'.
No path or device is specified.
Try `/usr/sbin/burg-probe --help' for more information.
dpkg: error processing burg-theme-what-am-i (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 burg-theme-cateyes
 burg-theme-what-am-i
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ssbijarnia on 2013-04-20
Please help me with error..I am not able to install any programm.

surendra@surendra-HP-Pavilion-dm4-Notebook-PC:~$ sudo apt-get purge burg-theme-cateyes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  burg-theme-cateyes burg-theme-what-am-i
0 upgraded, 0 newly installed, 2 to remove and 46 not upgraded.
2 not fully installed or removed.
After this operation, 6,201 kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: warning: files list file for package 'ubuntu-mono' missing; assuming package has no files currently installed
(Reading database ... 371021 files and directories currently installed.)
Removing burg-theme-cateyes ...
Generating burg.cfg ...
/usr/sbin/burg-probe: error: cannot stat `/boot/burg/locale'.
No path or device is specified.
Try `/usr/sbin/burg-probe --help' for more information.
dpkg: error processing burg-theme-cateyes (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing burg-theme-what-am-i ...
Generating burg.cfg ...
/usr/sbin/burg-probe: error: cannot stat `/boot/burg/locale'.
No path or device is specified.
Try `/usr/sbin/burg-probe --help' for more information.
dpkg: error processing burg-theme-what-am-i (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 burg-theme-cateyes
 burg-theme-what-am-i
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by matt_symes on 2013-04-20
Please do not create multiple threads on the same subject.

It diutes community effort and increases the staff's workload.

**Threads merged.**

---

### Post by matt_symes on 2013-04-20
Hi

It's looking for a file, cannot find it and failing while trying to purge.

Open a terminal and type

```
sudo touch /boot/burg/locale
```

Then try to purge as you did before. Post back if it works.

> dpkg: warning: files list file for package 'ubuntu-mono' missing; assuming package has no files currently installed

You also have this warning to address.

Kind regards

---

