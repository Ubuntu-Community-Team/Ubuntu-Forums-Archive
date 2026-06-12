---
title: "Error 100 with dpkg"
date: 2016-02-18
forum: Installation &amp; Upgrades
---

### Post by Lucas_Ansei on 2016-02-18
I'm a newbie migrating from Windows coding to Ubuntu, but once I  logged onto my machine there was this error with dpkg which is  preventing me from installing any packages. I might have messed up while  installing previous packages and etc.
  I'm using Ubuntu 15.10 btw.
  ```
    E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
    root@lucas-G750JX:~# apt-get -f install
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    Correcting dependencies... Done
    The following extra packages will be installed:
      dpkg update-notifier update-notifier-common
    The following NEW packages will be installed:
      dpkg
    The following packages will be upgraded:
      update-notifier update-notifier-common
    2 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
            Need to get 0 B/2.297 kB of archives.
    After this operation, 6.770 kB of additional disk space will be used.
    Do you want to continue? [Y/n] y
    Could not exec dpkg!
    E: Sub-process /usr/bin/dpkg returned an error code (100)

```  Tried to imput ls -l /usr/bin/

  ```
   root@lucas-G750JX:~# ls -l /usr/bin/dpkg
   ls: cannot access /usr/bin/dpkg: No such file or directory

```  Any tip on how to solve this?

---

### Post by bapoumba on 2016-02-19
Hello,

Maybe here ?
[http://ubuntuforums.org/showthread.php?t=1856256](http://ubuntuforums.org/showthread.php?t=1856256)
[http://ubuntuforums.org/showthread.php?t=2232313](http://ubuntuforums.org/showthread.php?t=2232313)

Edit : Moved the thread to Installation & Upgrades.

---

