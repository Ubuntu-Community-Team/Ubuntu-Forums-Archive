---
title: "Grub problem..!"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by Saikarthik on 2008-08-30
system restarts when i select "windows" in grub...
this started happening after a sudden power off from U.P.S...
now i'm able to log only in ubuntu..
im new to ubuntu please help me out to log in into windows..

---

### Post by Herman on 2008-08-30
:) Hello Saikarthik,
> this started happening after a sudden power off from U.P.S...
now i'm able to log only in ubuntu.. A sudden power off is bad for your file system. If you were running Windows when that happened then it could be that your Windows file system needs repairing. You should be able to fix that by running CHKDSK/R from a [Windows XP Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm").
If I have guessed correctly and that's what your problem is, that is not a GRUB problem, it has nothing to do with GRUB and it has nothing to do with Ubuntu, but hard shutdowns can cause problems in any computer.
Hard shutdowns can also damage your hard disk, sometimes permanently, but I hope you will be lucky and the file system check will be all you need.
At least it seems as if the Ubuntu area of your hard disk is still okay, and that's a good sign.

---

### Post by Herman on 2008-08-30
I see that you also have another thread in 'General Help' with the same name: [GRUB Problem...!]("http://ubuntuforums.org/showthread.php?t=905162")

---

