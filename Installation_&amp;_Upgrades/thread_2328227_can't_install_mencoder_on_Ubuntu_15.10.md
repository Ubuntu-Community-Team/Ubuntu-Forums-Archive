---
title: "can't install mencoder on Ubuntu 15.10"
date: 2016-06-18
forum: Installation &amp; Upgrades
---

### Post by Robert_Gaines on 2016-06-18
I have Ubuntu 15.10. I wanted to install mencoder, but the dependencies on my system are too advanced for it. I like using mencoder, but I needed to upgrade to Ubuntu 15.10. I don't want to break something else so is there another way to get it running? The only thing I can think of at this time is running Ubuntu 14.04 in a virtual environment, but that seems a little extreme. If I'm stuck with that option, should I use amd64 or 32 bit? I have amd64?

---

### Post by TheFu on 2016-06-19
Support for 15.10 ends shortly. Best to either stay with 14.04 or move to 16.04.

Didn't have any issues here installing it a few seconds ago:
```
$ sudo apt install mencoder
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  mplayer-doc
The following NEW packages will be installed:
  mencoder
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 801 kB of archives.
After this operation, 2,834 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 mencoder amd64 2:1.2.1-1ubuntu1 [801 kB]
Fetched 801 kB in 0s (1,247 kB/s)  
Selecting previously unselected package mencoder.
(Reading database ... 277289 files and directories currently installed.)
Preparing to unpack .../mencoder_2%3a1.2.1-1ubuntu1_amd64.deb ...
Unpacking mencoder (2:1.2.1-1ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up mencoder (2:1.2.1-1ubuntu1) ...
```

Seems to be working.  
```
$ more /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04 LTS"

```

I've never run 15.10. I only install LTS releases here. Sorry.

---

