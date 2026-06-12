---
title: "Boot problems with Ubuntu 13.04"
date: 2013-10-05
forum: Installation &amp; Upgrades
---

### Post by will10 on 2013-10-05
I'm fairly new to Ubuntu/Linux in general so please excuse me if I ask something obvious or stupid.  I've installed ubuntu 13.04 on a seperate harddrive than my Windows 7 install, and run the boot repair, yet my bios will not recognize the hardrive I have GRUB and Ubuntu installed on as bootable in the boot priorities menu.  Even if I choose to boot striaght to that drive, it will boot straight into Winodows 

This is the link that the boot repair gave me [http://paste.ubuntu.com/6197446/](http://paste.ubuntu.com/6197446/) but I obviously don't know what to do with or make of it, so I was wondering if anyone had any idea what's keeping it from booting.

---

### Post by ryanvade on 2013-10-05
According to that link, 
HDD 1 has Windows 7
HDD 2 has Ubuntu
USB HDD 1 is a 1 Tb Seagate Barracuda

If you disconnect the USB HDD and the Windows HDD, can you boot Ubuntu?

---

### Post by will10 on 2013-10-05
I considered doing that, but wanted to make sure It wouldn't interfere with GRUB or anything like that.

---

### Post by ryanvade on 2013-10-05
Removing the other HDDs should not cause any issues.   This is just to make sure grub is working properly.

---

### Post by will10 on 2013-10-05
> **ryanvade said:**
> Removing the other HDDs should not cause any issues.   This is just to make sure grub is working properly.

It fails to boot anything when the other hard drives are unplugged, does this mean grub is installed incorrectly or the entire OS?

---

