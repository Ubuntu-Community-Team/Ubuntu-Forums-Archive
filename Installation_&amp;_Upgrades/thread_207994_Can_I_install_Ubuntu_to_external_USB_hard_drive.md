---
title: "Can I install Ubuntu to external USB hard drive?"
date: 2006-07-02
forum: Installation &amp; Upgrades
---

### Post by cptvitamin on 2006-07-02
If I have an internal HD with Windows on it, Can I install Ubuntu to an external USB hard drive and choose which OS to boot to at boot time?

---

### Post by acorn22 on 2006-07-02
First off, Welcome! These forums are a great place to get help (the main reason I first looked at Ubuntu is because of the support)

Anyways, the answer is Yes. Mabye.

First off you need to go into your bios (restart and hold a key, it should tell you. f2 is mine) and make sure you can "boot from usb" I know on my box it won't give you the option unless the os is present, ie: without a boot cd in, i couldn't select boot from cd first.

Ok, if your computer is a p4-ish, you should be ok. (pentium 4) next, download ubuntu desktop cd and burn it to a disk. Make sure the disk is bootable, (see 1,000 other topics in here about it) and put the stick in (for later).

 Restart with the boot cd in and you should get a big Ubuntu picture and some options. Select the top one. It's called install or something. Then you will get a desktop envirnment. Here you can play around with the os. Then, on the desktop there is an ison that says "install". Click it. Go thru the steps but when It asks where to install it, select the usb drive. It will ERASE ALL DATA from the drive. 

Then to boot, go into bios (see step one) and make sure "USB" is set to the first thing to boot up. Then just start up and you will have linux.

As to choose at boot, you will have to get into GRUB or Lilo which I know nothing about...

NOTE: I myself am a semi-noob. Wait until someone else posts that I am in fact right. Though I have done it before, there could be other factors I don't know about :)

---

### Post by hanzomon4 on 2006-07-12
This worked for me [link]("http://ubuntuforums.org/showthread.php?t=80811&highlight=breezy+usb+boot")

---

