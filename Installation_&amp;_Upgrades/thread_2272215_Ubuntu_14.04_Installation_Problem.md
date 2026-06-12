---
title: "Ubuntu 14.04 Installation Problem"
date: 2015-04-04
forum: Installation &amp; Upgrades
---

### Post by patrickbhgr on 2015-04-04
Hi everyone, so I decided to reinstall Ubuntu 14.04 today, but for some reason it is booting up into grub minimal bash. I've installed Ubuntu 14.04 before on the same pc, but this is the first time that it is redirecting to grub. 

I have two SSD. the first one contains windows while the second one should contain Ubuntu. I'm not to familiar with grub, however when I write '**ls**',
I get 
[HTML]error: failure reading sector 0xe0 from hd1
error: failure reading sector 0x0 from hd1   [/HTML]

I assume h1 refers to the second SSD, the one I'm using to install Ubuntu. hd0 does show up, and I'm sure that it's the one that contains windows since the number of partitions do match up. hd3 (my external HDD) and hd4 (I suspect that it might be my usb) also show up. 


if I enter exit, Windows loads. What should I do? some say to use a live CD, though I'm not sure about what I'm expected to do with it.
**ps**: I've tried to follow [http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293) but I can't access hd1 of course. 

**TLDR: **I'm not able to access Ubuntu after installation, grub bash loads, failure reading hd1 when entering **ls**

---

### Post by oldfred on 2015-04-04
Best to see details, post link to summary report.
You can easily install to Ubuntu live installer.
But do not run any auto fix. That just installs grub to every drive's MBR, and you want to keep a grub boot loader in the MBR of the Windows drive. Advanced mode lets you choose an install and which drive to install a boot loader.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by patrickbhgr on 2015-04-05
I don't understand. what should I do? I can't install boot repair since I can't access Ubuntu

---

### Post by oldfred on 2015-04-05
You cannot boot the flash drive or DVD you used to install?

---

### Post by patrickbhgr on 2015-04-07
Hey, I found a solution. It was really down to what program I used to create a bootable usb. I used win32 disk imager ([http://sourceforge.net/projects/win32diskimager/](http://sourceforge.net/projects/win32diskimager/)) instead of Universal USB installer ([http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)). I've used UUSB before, so I assume it might be a temporary bug. Thank you oldfred nonetheless!

---

