---
title: "apt-get install not working"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by anonim on 2007-04-20
I just finished a command-line install (from the alternate CD) of Feisty Fawn.

I'm trying to get my Atheros wireless card to work. I found the following resource online:
[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

During the process, two of the steps are to install the bin86 and the sharutils packages. However, neither of the installs work successfully. Here is what I get:

```
root@xxxxx:/# apt-get -y install build-essential bin86
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package bin86
root@xxxxx:/# apt-get -y install sharutils
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package sharutils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source.
E: Package sharutils has no installation candidate
root@xxxxx:/#
```

My /etc/apt/sources.list is the default that comes with the installation. I tried downloading the two packages and then adding an entry in the sources.list, but this also didn't work (maybe I didn't do it right - I'm new to linux).

The Ubuntu installation detected my LAN connection and set it up automatically. I can successfully ping us.archive.ubuntu.com.

What do I need to do to get these packages installed?

EDIT: I should also note that I don't know if the restricted modules are installed by default or not. This is what I get when I try to install it:
```
root@xxxxx:/# apt-get install linux-restricted-modules-`uname -r`
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-restricted-modules-2.6.20-15-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@xxxxx:/#
```

---

### Post by spin2cool on 2007-04-20
The restricted modules appear to be there.  Try editing your /etc/apt/sources.list file.  Uncomment the lines for universe, multiverse, etc.  Then run 'sudo apt-get update' to make sure you have the newest versions of all the lists.  Try again, after that.

---

