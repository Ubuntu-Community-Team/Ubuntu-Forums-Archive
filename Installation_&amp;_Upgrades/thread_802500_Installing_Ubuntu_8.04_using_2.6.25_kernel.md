---
title: "Installing Ubuntu 8.04 using 2.6.25 kernel"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by arribastan on 2008-05-21
Okay, my question is probably rather weird, so bear with me.

I have a computer running two hard drives in raid 1 off of a Highpoint RocketRaid 3120 card. According to the Highpoint website, the card's drivers are in the 2.6.25 kernel. Ubuntu has packages available in non-official repositories for the 2.6.25 kernel, but the install CD is on the 2.6.24 kernel, which cannot see my drives and therefore cannot install. Even if I were to install the new driver, the live cd would want to reboot, and then I would be back where I started.

Is there any way I can get Ubuntu to install to my computer?

Also, I have Windows Vista installed on another partition, and a complete format or removing one drive from the RAID card to install to it isn't really an option. Highpoint's site also has drivers for FC, RHEL, and SUSE if that helps.

---

### Post by wumpus on 2008-05-21
My best guess is to follow the guide in the "ubuntu fakeraid howto", with whatever changes are needed (I wouldn't be surprised if it is fakeraid to begin with and needs less changes).

To get the thing to boot, it sounds like you will need the new kernel - instructions here:[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

IMPORTANT NOTE:  I didn't have enough space using the live cd to compile or unpack the kernel, so I had to use the chroot /target scheme used in the fakeraid howto.  I can't say how well 2.6.25 works, I compiled with 2.6.25.7 and am working fine (I needed to force a few modules enabled for software raid).

---

### Post by sniper910 on 2008-05-21
how much ram do you have?

---

### Post by zvacet on 2008-05-22
Try [this]("http://www.ubuntugeek.com/automatically-compile-and-install-the-latest-kernel-using-kernelcheck-in-ubuntu.html") to get latest kernel.

---

