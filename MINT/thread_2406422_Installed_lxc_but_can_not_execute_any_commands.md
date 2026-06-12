---
title: "Installed lxc but can not execute any commands"
date: 2018-11-20
forum: MINT
---

### Post by yzfrr7 on 2018-11-20
NOTE: I am running Linux Mint Sylvia

I am attempting to install lxc

I su'd to root and ran the following command: 

```

# sudo apt install lxc
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  lxc
0 upgraded, 1 newly installed, 0 to remove and 453 not upgraded.
Need to get 2,912 B of archives.
After this operation, 69.6 kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/main amd64 lxc all 3.0.2-0ubuntu4~16.04.1 [2,912 B]
Fetched 2,912 B in 0s (26.0 kB/s)
Selecting previously unselected package lxc.
(Reading database ... 212358 files and directories currently installed.)
Preparing to unpack .../lxc_3.0.2-0ubuntu4~16.04.1_all.deb ...
Unpacking lxc (3.0.2-0ubuntu4~16.04.1) ...
Setting up lxc (3.0.2-0ubuntu4~16.04.1) ...

```

**I THINK THE PROBLEM MIGHT BE HERE**: it unpack and sets up lxc but I see no talk about installation, in any case ... 

To check if it has been installed I run the following command: 
```

# lxc -ls
The program 'lxc' is currently not installed. You can install it by typing:
apt install lxd-client

```

By this stage I am curious so I  run the following:

```

# sudo apt-cache policy lxc
lxc:
  Installed: 3.0.2-0ubuntu4~16.04.1
  Candidate: 3.0.2-0ubuntu4~16.04.1
  Version table:
 *** 3.0.2-0ubuntu4~16.04.1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/main i386 Packages
        100 /var/lib/dpkg/status
     2.0.8-0ubuntu1~16.04.2 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages
     2.0.7-0ubuntu1~16.04.2 500
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 Packages
     2.0.0-0ubuntu2 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main i386 Packages

```


To understand the policy command shown above I took a look at the man page for  apt_preferences saw the following:
         priority 100           to the version that is already installed (if any) and to the versions coming from archives which in
           their Release files are marked as "NotAutomatic: yes" and "ButAutomaticUpgrades: yes" like the Debian
           backports archive since squeeze-backports.


       priority 500
           to the versions that do not belong to the target release.

I interpret the above as saying that all the packages marked as 500 are not part of/not required by lxc?
Only one package has been marked with 100 aka. installed that is /var/lib/dpkg/status?

I decided to try another means to determine if the package had been installed:

```

# dpkg -l lxc
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                    Version          Architecture     Description
+++-=======================-================-================-===================================================
ii  lxc                     3.0.2-0ubuntu4~1 all              Transitional package - lxc -> lxc-utils

```

This also leads me to believe that lxc has been installed.
I am out of ideas so I remove lxc:

```

# sudo apt remove lxc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bridge-utils liblxc-common liblxc1 lxc-utils
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  lxc
0 upgraded, 0 newly installed, 1 to remove and 453 not upgraded.
After this operation, 69.6 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 212361 files and directories currently installed.)
Removing lxc (3.0.2-0ubuntu4~16.04.1) ...

```

I try installing again, same results as shown above, can anyone explain what is going on or what state I am in?

Thank you

---

### Post by wildmanne39 on 2018-11-20
*Thread moved to **MINT for a more appropriate fit**.*

---

### Post by yzfrr7 on 2018-11-21
Apologies, new to the forums. Thanks wildmanne39

---

### Post by spjackson on 2018-11-21
The Ubuntu package lxc provides a set of commands beginning with lxc- e.g. lcx-create, lxc-ls, lxc-start, lxc-stop etc. but does not provide an lxc command. After installing the lxc package, you could get a list by
```

ls /usr/bin/lxc*

```
I can't be certain that the same applies to Linux Mint Sylvia but it may well do.

---

### Post by yzfrr7 on 2018-11-21
Great thanks, I found those commands based on your advice but something is still not right (see below):

```

$ ls /usr/bin/lxc*
/usr/bin/lxc-attach       /usr/bin/lxc-destroy   /usr/bin/lxc-stop
/usr/bin/lxc-autostart    /usr/bin/lxc-device    /usr/bin/lxc-top
/usr/bin/lxc-cgroup       /usr/bin/lxc-execute   /usr/bin/lxc-unfreeze
/usr/bin/lxc-checkconfig  /usr/bin/lxc-freeze    /usr/bin/lxc-unshare
/usr/bin/lxc-checkpoint   /usr/bin/lxc-info      /usr/bin/lxc-update-config
/usr/bin/lxc-config       /usr/bin/lxc-ls        /usr/bin/lxc-usernsexec
/usr/bin/lxc-console      /usr/bin/lxc-monitor   /usr/bin/lxc-wait
/usr/bin/lxc-copy         /usr/bin/lxc-snapshot
/usr/bin/lxc-create       /usr/bin/lxc-start

```

If I try create a container I don't encounter any issues:
```

$ /usr/bin/lxc-create testContainer

```

But if I try to get info on this newly created container I get the following message:
```

$ /usr/bin/lxc-info testContainer
testContainer doesn't exist

```

Now I am a total noob with containers, this is my first time experimenting so I am not entirely sure of where I go from here, any ideas?

---

### Post by wildmanne39 on 2018-11-21
No worries!

---

### Post by spjackson on 2018-11-22
> **yzfrr7 said:**
> 

If I try create a container I don't encounter any issues:
```

$ /usr/bin/lxc-create testContainer

```

But if I try to get info on this newly created container I get the following message:
```

$ /usr/bin/lxc-info testContainer
testContainer doesn't exist

```

Now I am a total noob with containers, this is my first time experimenting so I am not entirely sure of where I go from here, any ideas?
I am not familiar with lxc. The Getting Started page [https://linuxcontainers.org/lxc/getting-started/](https://linuxcontainers.org/lxc/getting-started/) indicates some set up to do before creating your first container.

---

