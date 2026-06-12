---
title: "Trouble booting Ubuntu from CD"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by Lyreat on 2007-12-29
Alright, I'm trying to boot Ubuntu from a CD. I succesfully get the boot menu when I tell BIOS to boot from CD, but when I boot I just get a blank desktop environment. Even if I boot into safe mode it does this. I've let it sit for about 30 minutes or so and the computer isn't even trying to do anything. Can someone point me in the right direction here?

---

### Post by taurus on 2007-12-29
What is the spec of your machine?  Is it Gutsy LiveCD (desktop CD)?

---

### Post by Lyreat on 2007-12-29
Yeah, it's Ubuntu 7.10.

2.4 ghz Compaq, 40G HDD, 512 memory, integrated graphics.

---

### Post by taurus on 2007-12-29
I assume that would be Intel onboard graphic controller one.  Are you planning to install Gutsy on your machine?  You can always try the alternate CD.

---

### Post by Lyreat on 2007-12-29
Yeah, it's that Intel Graphics Controller. I can't get on to check what it is exactly without cracking the case because it was running XP and died. 
And yes, I'm thinking about installing. And since I'm kinda new here, what is the alternate CD?

---

### Post by taurus on 2007-12-29
> 
Alternate install CD

The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

    * creating pre-configured OEM systems;
    * setting up automated deployments;
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    * installs on systems with less than about 320MB of RAM (although note that low-memory systems may not be able to run a full desktop environment reasonably). 

In the event that you encounter a bug using the alternate installer, please file a bug on the debian-installer package.

There are two images available, each for a different type of computer:


[http://www.gtlib.gatech.edu/pub/ubuntu-releases/7.10/ubuntu-7.10-alternate-i386.iso](http://www.gtlib.gatech.edu/pub/ubuntu-releases/7.10/ubuntu-7.10-alternate-i386.iso)

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/7.10/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/7.10/)

---

