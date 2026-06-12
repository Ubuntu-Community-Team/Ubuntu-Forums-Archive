---
title: "[SOLVED] Problem with linux-headers"
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by BetterSense on 2008-10-09
I just installed fresh on a new laptop, Hardy Heron. I ran an update and upgrade. At the end of the upgrade I got this error

```
Errors were encountered while processing:
 linux-headers-2.6.24-19

```

Then when I went to install webcam software, it got stuck on linux-headers again somehow. I don't know what this means and why it's happening, or even what linux-headers is.

```
chaz@singularity:~$ apt-get install luvcview
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  luvcview
0 upgraded, 1 newly installed, 0 to remove and 24 not upgraded.
1 not fully installed or removed.
Need to get 49.8kB/8181kB of archives.
After this operation, 160kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com hardy/universe luvcview 20070512-3 [49.8kB]
Fetched 49.8kB in 0s (56.7kB/s)  
(Reading database ... 133836 files and directories currently installed.)
Preparing to replace linux-headers-2.6.24-19 2.6.24-19.41 (using .../linux-headers-2.6.24-19_2.6.24-19.41_all.deb) ...
Unpacking replacement linux-headers-2.6.24-19 ...

```

---

### Post by speed32219 on 2008-10-09
What are you upgrading from?   A fresh install with updates is about all that is needed.  Just confused over the word upgrade.

---

### Post by BetterSense on 2008-10-09
For some reason, as we all know, running apt-get update only updates the sources. You have to run apt-get upgrade to actually update the system. I updated the system.

I apparently had to run dpkg-configure -a or something.

---

