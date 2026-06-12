---
title: "Where does Grub reside ?"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by dptxp on 2007-04-23
When I install Ubuntu with dual boot, where does Grub reside ?
If I delete and format my C drive (primary partition) which has Windows XP, what will happen ?

---

### Post by packjamNL on 2007-04-23
Grub will install itself in the boot master record of your HD you install it on.
whn you want to install a dualboot with grub ( wich is easy to do ) It's better to 1st install windows if you want to, and then after windows your linux or ubuntu.iso, and not the other way around.
Then you'll find your bootloader, Grub.
Windows whipes clean the boot master record, there will be no more grub to find.

---

### Post by dptxp on 2007-04-23
I had XP. I have installed Ubuntu.I am dual booting, I plan to remove XP.
I want to know if if I reformat C drive (XP is there), will I damage anything ?

---

### Post by DracoPsycho on 2007-04-23
It varies:

If you plan to install XP there after format then you'll lose GRUB.

If you format the drive and leave it as data partition then you won't lose GRUB.

In other words, installing Windows will remove GRUB.

And as it was said earlier GRUB resides in boot master record of drive which is not formatted.

---

