---
title: "problem trying to remove a problem"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by wheresmything on 2010-06-09
i have installed a language pack that is giving me fits...i dont think it installed correctly or was corrupted during install...anyway, since then everytime i try to install or update something i get an error: 
software database is broken. it is impossible to install/remove software. run apt-get install -f to fix the problem.

well, i did, and this is what i get...





root@james-laptop:/home/james# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  language-pack-kde-sr-base
0 upgraded, 0 newly installed, 1 to remove and 46 not upgraded.
1 not fully installed or removed.
After this operation, 14.3MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 343126 files and directories currently installed.)
Removing language-pack-kde-sr-base ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing language-pack-kde-sr-base (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 language-pack-kde-sr-base
E: Sub-process /usr/bin/dpkg returned an error code (1)

i have tried other  removal tools,,,gconf cleaner and bleachit with similar results...is there any help out there?

---

