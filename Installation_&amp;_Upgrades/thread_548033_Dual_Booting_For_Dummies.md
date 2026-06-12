---
title: "Dual Booting For Dummies"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by eob on 2007-09-10
I've got a pretty awesome set-up going here...

HDD1:
Windows XP

HDD2:
Linux Ubuntu
Linux Puppy

If I yank the cable for the first HDD, the second HDD automatically takes over (GRUB) and asks me which version of Linux I want to boot to.

But... If I leave the first hard drive plugged in, it will obviously just boot Windows.

I tried the obvious thing and edited boot.ini with no success. It seems to just deal with various versions of Windows. There has to be a way to get Windows to boot into Puppy/Ubuntu without having to physically yank cables **or** installing MBR software like LILO to the first HDD? 

I don't want to go swapping HDD's around etc, much prefer to just have Linux pop up in the boot.ini menu when the first XP HDD boots.

Any suggestions?

---

### Post by Pumalite on 2007-09-10
Grub is a much better boot loader than the one from Windows. I would install it to the MBR and be done with it. You would have a menu to boot all three.

---

### Post by eob on 2007-09-10
Terrified of mucking up my Windows MBR...

---

### Post by merlinus on 2007-09-10
You can easily reinstall it via xp cd in recovery console, or supergrub.

Terrified?  Of computers?  C'mon!!

---

### Post by eob on 2007-09-11
Actually, thou is right, I forgot about the MBR recovery via the XP CD. You rock! Thanks!

---

### Post by Pumalite on 2007-09-11
Good. You are almost an Ubunter now.

---

