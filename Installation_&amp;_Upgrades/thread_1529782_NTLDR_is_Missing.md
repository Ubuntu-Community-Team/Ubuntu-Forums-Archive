---
title: "NTLDR is Missing"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by MadDawg010 on 2010-07-12
Alright, I've just installed Windows XP on my second hard drive, which is /dev/sdb. I have an empty NTFS partition reserved for Windows 7 on the first drive, which is /dev/sda1. Ubuntu is located on /dev/sda5, and I'm trying to get Gentoo to work on /dev/sda6, and I can't figure out how to add it to Grub2, but that's a different issue I'll worry about later. 

The *main* issue here is that when I installed XP, it, of course, rewrote the MBR, deleting Grub2. After that, I popped in the Alt-install CD and restored Grub, but when I tried to boot into Windows, I just get a black screen that reads something like "NTLDR is Missing. Press Ctrl+Alt+Del to restart." Performing fixmbr allows me to boot into Windows again, but that deletes Grub, which makes Linux unbootable.

How do I restore Grub2 without breaking Windows? I'm thinking about moving NTLDR and boot.ini to the second drive, but I wanna see if there's an alternative solution.

---

### Post by new_tolinux on 2010-07-12
NTLDR is placed on the first readable partition.
In this case that means it's placed on the Windows 7-partition (expecting the Ubuntu installation uses the ext3/4 filesystem, which is used by default).

That means that pointing towards the W7-partition should enable you to boot XP.
Although it _can_ mean that with the installation of XP your W7 has become unreachable.

Edit:
Not a real anwer to the grub2-part, I'll leave that to the experts before I say something that ruins your installation.

---

### Post by oldfred on 2010-07-13
You may be able to repair the XP partition. Put boot flag on it and try XP repairs. Otherwise you will have to boot thru the win7 partition.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by MadDawg010 on 2010-07-14
Thanks for the info. I found that the boot flag on the second drive is not set. I'll try to set it and see what happens.

---

### Post by MadDawg010 on 2010-07-15
After all kinds of messing around with the boot sector and the OS itself, Windows just refuses to cooperate. I did try to do a **bootcfg /rebuild**, but my drive had bad sectors that kept the command from running. I eventually just gave up and installed Windows in a VM. I think I could hide my first HDD via some bios options, but I'll try that another day. Thanks for the assistance, guys.

---

