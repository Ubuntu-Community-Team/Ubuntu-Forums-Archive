---
title: "GRUB Loader Options"
date: 2011-06-06
forum: Installation &amp; Upgrades
---

### Post by here4help on 2011-06-06
I am very much new to Ubuntu (Linux) OS which a colleague of my son recently installed on my laptop already with Windows Vista - Premium  Home Edition.
 
Not being familiar at all with the usage, it's only on occasional basis that I play around it to familiarize myself. I noticed an indication at the left bottom on the screen to upgrade which I did.
 
When the Ubuntu was initially installed, The GRUB Loading screen listed the following booting options:
Ubuntu, Linux 2-6-31-14-generic
Ubuntu, Linux 2-6-31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 15200)
Windows Vista (loader) (on /dev/sda1
Windows Vista (loader) (on /dev/sda2)
 
After carrying out the "Update" process, I now have the following options:
Ubuntu, Linux 2-6-31-23-generic
Ubuntu, Linux 2-6-31-23-generic (recovery mode)
Ubuntu, Linux 2-6-31-14-generic
Ubuntu, Linux 2-6-31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 15200)
Windows Vista (loader) (on /dev/sda1)
Windows Vista (loader) (on /dev/sda2)
 
Questions are: (1) How do I remove the original Linux 2-6-31-14 options?
and
(2) How do I make Windows Vista as the first option?
 
Thanks to all who may help me to understand the Linux better.

---

### Post by oldfred on 2011-06-06
Welcome to the forums.

We normally suggest you keep two kernals, just in case one has issues you have a working backup.

You can permanently remove using synaptic. But be sure not to remove your current version or you will not be able to reboot.

Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

An easy way to update grub's settings/menus.
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
The Grub 2 Guide (formerly Grub 2 Basics) manual way
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

