---
title: "Getting GRUB back!"
date: 2005-10-30
forum: Installation &amp; Upgrades
---

### Post by ubuntufella on 2005-10-30
Hi. Today I installed Windows XP Professional on my (well it's mum's) laptop and I suppose it has written the Windows XP boot loader over grub and I can no longer boot to my Ubuntu desktop. Is there a way to get GRUB back, or better still, a way to get the Microsoft boot loader to boot my Ubuntu desktop? Thanks in advance.

---

### Post by Xian on 2005-10-30
Both are possible, but much easier to just reinstall grub. Generally most people will use a Linux LiveCD (such as Knoppix), mount the Ubuntu partition as rw, chroot into that installation, and issue the command to place grub back to the MBR.

If not too much of this is clear to you I'd just do a forum search on the topic. There have been many threads on how to do this, and me doing another step-by-step would be overkill. But in any case it is not difficult to perform.

---

### Post by aysiu on 2005-10-30
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

