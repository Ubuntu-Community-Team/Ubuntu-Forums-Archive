---
title: "Installation on RocketRAID 2640X4 RAID-0"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by jinxy2 on 2009-12-31
Hi guys,

I have been running Ubuntu since version 5 and I think it really is the best *NIX OS if you're into bleeding edge and so far I've had no problems, until now!

Anyhow, I tried installing 64bit 9.10 (Alternate) on my previous RAID-0 setup ran by Intel Matrix controller (FakeRAID) and it went down the drain, my Windows 7 partition would not boot anymore and could not be repaired nor found by Windows install. Luckily, I could save my files using Ubuntu Live-CD *yay!*
This experince made me look into some real RAID controller and I bought a HighPoint RocketRAID 2640X4 to run both Win 7 and Ubuntu 9.10 on separate partitions. Unfortunately it requires drivers when installing OS. Installation on Windows 7 was a breeze but not on Ubuntu...

HighPoint ([http://www.highpoint-tech.com/USA/bios_rr2640.htm](http://www.highpoint-tech.com/USA/bios_rr2640.htm)) have provided both open-source and installation script for Ubuntu 8.04, not 9.10. I was able to compile a module using their open-source drivers and insmod it using live-CD and build-essential package installed. **THE question is how do I "install" this kernel module during installation so that harddrive is found by installation program and also make sure it is always loaded in the future after OS has been installed?** I also assume as soon as I hit a kernel upgrade it will break again?

---

### Post by dstew on 2009-12-31
I think you can get a command line for the Alternate Install CD before installing, and maybe there you can do insmod for the driver. Then, start the installation. I don't know about making it load at bootup, but I am pretty sure that can be solved somehow. The new grub can insert a kernel module at bootup, I think. I see the insmod command in some grub 2 menu items. I think the module would probably have to be recompiled/reinstalled with each kernel upgrade.

---

### Post by jinxy2 on 2009-12-31
OK, about what I though... Regarding module compilation, do I need to re-compile it every time kernel is updated or can I compile it once and then use it on any kernel that comes down the drain from canonical?

---

### Post by dstew on 2009-12-31
I am not sure. My guess is that the kernel updates are not so significant that you would need to compile with each one. I mean, 2.6.24-14 to 2.6.24-16 is probably not big enough to cause a problem. But 2.6.24 to 2.6.26 probably would be. You would just have to see.

---

### Post by Petch on 2010-10-10
I don't mean to thread resurrect, but my issue relates to this.

I am a linux/unix nub, but I am doing what I can to make the change!!  I have a RocketRaid 2640X4 card and I just installed Ubuntu 10.04 LTS.  My issue is, is that at this point I have no idea how to get this card working.  It appears that Jinxy2 has gotten his working, and I was just looking for some proper instructions on how to do this.  I have an existing 4TB (3TB usable) RAID 5 array that currently exists with this card, and Im trying not to lose it!

Thanks!

---

### Post by krutoileshii on 2011-10-10
> **Petch said:**
> I don't mean to thread resurrect, but my issue relates to this.

I am a linux/unix nub, but I am doing what I can to make the change!!  I have a RocketRaid 2640X4 card and I just installed Ubuntu 10.04 LTS.  My issue is, is that at this point I have no idea how to get this card working.  It appears that Jinxy2 has gotten his working, and I was just looking for some proper instructions on how to do this.  I have an existing 4TB (3TB usable) RAID 5 array that currently exists with this card, and Im trying not to lose it!

Thanks!

[http://ubuntuforums.org/showthread.php?t=1856162](http://ubuntuforums.org/showthread.php?t=1856162)  

this is how i got it to compile.

to get ubuntu installed, you will have to start the live cd and then create you will have to compile the driver in the live environment. Once compiled, you install it and load it. Then proceed with the normal install process. do not reboot as you will have to chroot into the fresh install to install the driver there and to recreate the init images.

---

