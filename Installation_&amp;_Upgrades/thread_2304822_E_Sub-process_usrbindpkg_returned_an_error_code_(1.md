---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1) - libunity-webapps0"
date: 2015-11-30
forum: Installation &amp; Upgrades
---

### Post by Girish_Aligati on 2015-11-30
Hi ,

I have upgraded my Ubuntu version from 12.04 tor 14.04, it was not successful(as my system hung in the middle of installation) but I have somehow managed to upgrade from the terminal(ctrl + alt + F1) using upgrade and update commands.

There are few errors that I am unable to remove/update them.

Below is the output
```

girish@girish-Lenovo-IdeaPad-Y550:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libunity-webapps0 : Depends: unity-webapps-service but it is not installed
E: Unmet dependencies. Try using -f.
girish@girish-Lenovo-IdeaPad-Y550:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
girish@girish-Lenovo-IdeaPad-Y550:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  unity-webapps-service
The following NEW packages will be installed:
  unity-webapps-service
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 142 kB of archives.
After this operation, 500 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
WARNING: The following packages cannot be authenticated!
  unity-webapps-service libunity-webapps0
Install these packages without verification? [y/N] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/main unity-webapps-service amd64 2.5.0~+14.04.20140409-0ubuntu1 [82.9 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty/main libunity-webapps0 amd64 2.5.0~+14.04.20140409-0ubuntu1 [59.1 kB]
Fetched 142 kB in 1s (101 kB/s)         
Selecting previously unselected package unity-webapps-service.
(Reading database ... 538595 files and directories currently installed.)
Preparing to unpack .../unity-webapps-service_2.5.0~+14.04.20140409-0ubuntu1_amd64.deb ...
Unpacking unity-webapps-service (2.5.0~+14.04.20140409-0ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.40.2-0ubuntu1) ...
Processing triggers for libglib2.0-0:i386 (2.40.2-0ubuntu1) ...
Setting up unity-webapps-service (2.5.0~+14.04.20140409-0ubuntu1) ...
dpkg: error processing package libunity-webapps0 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
Errors were encountered while processing:
 libunity-webapps0
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by slickymaster on 2015-11-30
Try to follow apt suggestion. In a terminal window run the following command:```
sudo apt-get install --reinstall libunity-webapps0
```If it reinstall successfully, then run```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

