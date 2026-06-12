---
title: "Installing grub"
date: 2006-08-03
forum: Installation &amp; Upgrades
---

### Post by mirons on 2006-08-03
Hi everybody. Due to some hacking on the partition table I was forced to reinstall windows on my pc. Now the situation is that I have the win bootloader on the mbr but still all my Linux partitions on the hd (including /boot with properly configured menu.lst). Does somebody know how to reinstall in a clean way grub on the mbr using just windows and without messing things?
Thanks in advance.

---

### Post by Phasmagon on 2006-08-03
You have to boot from the live-CD and run from a terminal
grub-install (the drive or patrition you want the boot loader installed. e.x /dev/hda)

---

### Post by mirons on 2006-08-03
It doesn't work. It complains about a non valid disk for /boot
(the command I gave was "grub-install /dev/hdc" being hdc the disk where I have all system partitions. I tried also "grub-install /dev/hdc3", whic is my /boot partition but the result was the same. I think that perhaps there is some key word to make it install on tha master boot record. Somebody out there knows?)

---

### Post by confused57 on 2006-08-03
Here's a guide that might help:

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by mirons on 2006-08-03
> **confused57 said:**
> Here's a guide that might help:

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Thanks a lot!

---

