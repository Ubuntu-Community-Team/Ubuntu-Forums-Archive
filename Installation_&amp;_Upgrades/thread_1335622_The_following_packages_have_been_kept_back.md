---
title: "The following packages have been kept back:"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by xdemo on 2009-11-23
EDIT: restart fixed it, not sure why, but is now letting me install them.
-------------------

```
demo@foxy:~$ sudo apt-get  upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
demo@foxy:~$
```Ok, why am i getting this?
Not much of a problem, its just i'd rather be running the latest kernel patches etc.
I noticed while doing a fresh install of 32bit karmic on my old laptop, that while updating upon installation being finished, the kernel was at 2.6.31-15-generic.

And my desktop running 64bit, is still on 2.6.31-14-generic
Why are the packages being held back? o.o

Thanks in advance.

p.s about to restart after installing the updates that went through. could be my problem, however no restart notice was given. brb

---

### Post by lloyd_b on 2009-11-23
For future reference, "sudo apt-get dist-upgrade" should work around that problem.

From the 'apt-get' man page:> upgrade
           upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new
           versions available are retrieved and upgraded; [B]under no
           circumstances are currently installed packages removed, or packages
           not already installed retrieved and installed. New versions of
           currently installed packages that cannot be upgraded without
           changing the install status of another package will be left at
           their current version.[/B] An update must be performed first so that
           apt-get knows that new versions of packages are available.So if an upgrade requires removing a package, or installing a new package, then 'upgrade' won't do it.  'dist-upgrade', however, will intelligently do whatever is required to get the package(s) installed, including deleting packages or installing new packages.

Lloyd B.

---

