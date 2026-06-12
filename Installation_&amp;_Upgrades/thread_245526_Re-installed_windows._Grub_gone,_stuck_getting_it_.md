---
title: "Re-installed windows. Grub gone, stuck getting it back."
date: 2006-08-28
forum: Installation &amp; Upgrades
---

### Post by Visceral Monkey on 2006-08-28
OK, I had to re-install windows xp. Now, it obviously hosed my grub. Windows is setup on one drive and Ubuntu another, like so:

First hard drive:
/dev/sda1 = Windows

Second hard drive:
/dev/sdb1 = ext3
/dev/sdb2 = extended
/dev/sdb5 = linux-swap

I've looked at a few other threads talking about replacing grub, but I'm lost as to how to do this with two hard drives. Where exactly am I trying to reinstall grub to, /dev/sda1?

---

### Post by confused57 on 2006-08-28
You should be able to use the live cd with this "howto":
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Grub should find stage1 at root (hd1,0), which is sdb1.
You'd setup (hd0), which is sda.

---

### Post by Visceral Monkey on 2006-08-28
Thank you, it worked perfectly!

---

