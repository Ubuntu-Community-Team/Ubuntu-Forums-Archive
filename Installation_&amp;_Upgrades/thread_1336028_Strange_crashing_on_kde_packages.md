---
title: "Strange crashing on kde packages"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by TJoh311 on 2009-11-24
Hello,

 I was attempting to install envyng through the synaptic package manager when the system froze. Not exactly sure what happened, but, of course, the packages did not finish installing. Now whenever I try to use apt-get, I get the following.



```
root@troy-laptop:/home/troy# apt-get install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ia32-libs lib32asound2 lib32bz2-1.0 lib32gcc1 lib32ncurses5 lib32stdc++6
  lib32v4l-0 lib32z1 libc6-i386 nspluginwrapper
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs
  lib32asound2-plugins
The following packages will be REMOVED:
  kdebase-runtime kdepimlibs5 libknotificationitem1 libplasma3
The following NEW packages will be installed:
  flashplugin-installer ia32-libs lib32asound2 lib32bz2-1.0 lib32gcc1
  lib32ncurses5 lib32stdc++6 lib32v4l-0 lib32z1 libc6-i386 nspluginwrapper
0 upgraded, 11 newly installed, 4 to remove and 0 not upgraded.
37 not fully installed or removed.
Need to get 0B/34.2MB of archives.
After this operation, 126MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 144591 files and directories currently installed.)
Removing kdebase-runtime ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing kdebase-runtime (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing kdepimlibs5 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing kdepimlibs5 (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing libknotificationitem1 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing libknotificationitem1 (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing libplasma3 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing libplasma3 (--remove):
 subprocess installed post-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 kdebase-runtime
 kdepimlibs5
 libknotificationitem1
 libplasma3
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@troy-laptop:/home/troy# 

```

Never really had a problem like this before... Please help!

Thanks in advance.

---

