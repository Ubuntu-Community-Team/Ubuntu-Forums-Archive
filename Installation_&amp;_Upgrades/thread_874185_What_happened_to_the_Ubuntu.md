---
title: "What happened to the Ubuntu?"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by walkingonthesun on 2008-07-29
Like a few weeks back, I installed Ubuntu, and it was working fine. My computer's motherboard went screwy and I had to get a new one; the CD Drive / Floppy Drive / Hard Drive are still the same. Now, it just boots straight into XP rather than showing the GRUB loader. The Disk is still partioned and everything, and I think the Ubuntu stuff is still there... why's it like this though? Is there anything I can do to just delete the Ubuntu off, or just make it usable again...

---

### Post by Pumalite on 2008-07-29
Reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Sef on 2008-07-29
> Is there anything I can do to just delete the Ubuntu off, or just make it usable again...

Get [Super GRUB Disk]("http://www.supergrubdisk.org/").

To check if Ubuntu is still there:

Applications > Accessories > Terminal

then copy/paste or type this code:

```
sudo fdisk -l
``` small L

---

### Post by walkingonthesun on 2008-07-29
Ok, well, it looks like [**Ubuntu is still there**](http://img362.imageshack.us/img362/2223/screenshotky1.png) but it's not booting like I said... are you guys sure I need the grub loader? I've never fooled with Ubuntu before, so forgive my... ignorance...

---

### Post by Pumalite on 2008-07-29
Reinstall Grub

---

### Post by walkingonthesun on 2008-07-29
Fine, fine, I'll go try to reinstall grub.

---

### Post by steveneddy on 2008-07-29
> **walkingonthesun said:**
> Fine, fine, I'll go try to reinstall grub.

Good boy.

Let us know if you need any help.

---

### Post by walkingonthesun on 2008-07-29
Reinstalled it, and I got it working... went into Ubuntu, and it looks to work. Just have to fix a few things... Thanks? o_O

---

