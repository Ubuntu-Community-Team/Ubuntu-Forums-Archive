---
title: "To upgrade or not ???"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by jfl on 2008-05-07
[FONT="Comic Sans MS"]I am resting in the mountains of N. Georgia and getting bored.
Upgrading from 7.10 to 8.04 is increasingly itching !!!
However, I just have a DVD/CD-ROM reader so I have to do an on-line upgrade with[B] no possibility to burn a CD and my XP install CD is 800 miles away.
[/B]
I have an almost new Thinkpad running dual boot (grub) XP and Gutsy and a separate */home* partition.
The Gutsy install was a breeze ...

Question: Can a bad Ubuntu upgrade render my Windoze not accessible ?
I'd hate to spend 5 days without a computer  :confused:... yeah, Windoze is not great, but far better than nothing.

Thanks  [/FONT]

---

### Post by darc on 2008-05-07
> **jfl said:**
> [FONT="Comic Sans MS"]I am resting in the mountains of N. Georgia and getting bored.
Upgrading from 7.10 to 8.04 is increasingly itching !!!
However, I just have a DVD/CD-ROM reader so I have to do an on-line upgrade with[B] no possibility to burn a CD and my XP install CD is 800 miles away.
[/B]
I have an almost new Thinkpad running dual boot (grub) XP and Gutsy and a separate */home* partition.
The Gutsy install was a breeze ...

Question: Can a bad Ubuntu upgrade render my Windoze not accessible ?
I'd hate to spend 5 days without a computer  :confused:... yeah, Windoze is not great, but far better than nothing.

Thanks  [/FONT]


Shouldn't be able to, assuming you don't reinstall GRUB and lose your boot manager.  An online upgrade shouldn't touch your partitions at all, and it doesn't touch your boot loader (except for updating the list of kernels to point to the new kernels in /boot/grub/menu.lst which does not require re-installing GRUB)

That's not to say you may not have problems with the upgrade, but I can't think of any -reasonable- way that it would muck up your ability to run windows if you've already got it dual booting.

Good luck to you,
-darc

---

### Post by jfl on 2008-05-08
> **darc said:**
> Shouldn't be able to, assuming you don't reinstall GRUB and lose your boot manager.  An online upgrade shouldn't touch your partitions at all, and it doesn't touch your boot loader (except for updating the list of kernels to point to the new kernels in /boot/grub/menu.lst which does not require re-installing GRUB)

That's not to say you may not have problems with the upgrade, but I can't think of any -reasonable- way that it would muck up your ability to run windows if you've already got it dual booting.

Good luck to you,
-darc
Thanks !!!
I'll wait acouple more days, just in case.

---

### Post by cub on 2008-05-09
As said, it "shouldn't" be possible but if 15 years in the business has taught me something it's that things that shouldn't be possible usually occurs when you have no means to go back. I would wait. :D

---

