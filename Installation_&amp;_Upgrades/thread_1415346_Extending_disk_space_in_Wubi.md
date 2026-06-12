---
title: "Extending disk space in Wubi"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by Harrowcactus on 2010-02-24
I have installed Ubuntu 9.10 using Wubi. During the install I allocated 100Gb to Ubuntu, is there any way without reinstalling of extending this, I want to give Ubuntu another 50Gb.

---

### Post by oldfred on 2010-02-24
I do not have wubi. See this section. 
**[SIZE=1][B]How do I resize the virtual disks?**[/SIZE]
[/B]

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

If you are using wubi this much it may be time to consider a full install into its own partitions? Wubi runs on NTFS thru windows and is not totally separate from windows, but is a complete version of Ubuntu. It is intended to make it easy fro windows users to try out and use Ubuntu. but usually not for more than 6 months when the next upgrade is available.
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

### Post by sailthesea on 2010-02-24
> **Harrowcactus said:**
> I have installed Ubuntu 9.10 using Wubi. During the install I allocated 100Gb to Ubuntu, is there any way without reinstalling of extending this, I want to give Ubuntu another 50Gb.

If you are dedicating that kind of space to a virtual setup you should go ahead and dual boot If you can boot from a CD its easy enough I would guess you have a desktop with Vista so download the ISO and make a liveCD 
 Next crunch Vista down with a few defrags and clean things up then partition the drive out with enough space for both 
 You can move your data from from ubuntu to Host in Wubi which will put them on the Windows side of your drive
 Remember to backup as well and read up on the dual boot procedure
 Good luck!

---

