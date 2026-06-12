---
title: "Where do I download the Vmware Tools disk image?"
date: 2011-08-14
forum: Installation &amp; Upgrades
---

### Post by dandeliondream on 2011-08-14
I'm using vmware3.1.4 player with ubuntu10.04 guest. Host OS: windows 7. 
 
Where do I download the Vmware Tools disk image? I've searching for hrs...help

---

### Post by steve11911 on 2011-08-15
If this page doesn't satisfy please repost.

[http://www.sysprobs.com/install-ubuntu-1010-vmware-playerworkstation-working-vmware-tools](http://www.sysprobs.com/install-ubuntu-1010-vmware-playerworkstation-working-vmware-tools)

---

### Post by bigcreturns on 2011-08-16
Ensure for 11.04 server edition you have: make, gcc and the linux C header files installed.

sudo apt-get update

sudo apt-get install make

sudo apt-get install gcc

Then enter: 
uname -r

My kernel was: 2.6.38-10-generic

sudo apt-get install build-essential linux-headers-**2.6.38-10-generic**

Now run the vmware-install.pl script.

---

### Post by dandeliondream on 2011-08-16
Thanks!

---

