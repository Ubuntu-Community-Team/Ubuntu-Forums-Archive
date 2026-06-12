---
title: "Can I safely resize my XP partition?"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by ralphiekabo on 2006-08-27
I want to install Ubuntu onto my computer but, fool that I am, I made just one 80GB partition taking up the entire drive. Windows currently takes up around 25GB of that. Is it possible to safely reduce that partition to 40GB using GParted, then create the Ubuntu partitions in the empty space?

---

### Post by Klaidas on 2006-08-27
You should be able to do that when installing, when you come to partitioning :)

---

### Post by SkyNet2029 on 2006-08-27
Yes, it is possible and safe to do just that using Gparted. You will need to do two-three defragmentation runs from within Windows prior to all of your resizing, to ensure that all of your data on the drive is packed as tightly as possible to the front of the drive, plus it makes life for Gparted that much simpler. After the defrag runs, reboot using the Linux and partition away.
Oh, and don't forget to backup all the 'important' data prior to all of this. Not that I have ever experienced any file-system/Data corruption using Gparted, just that it's a good practice to follow, just in case.

---

### Post by ralphiekabo on 2006-08-27
Thankyou muchly. And yeah, I backed up all my important data (or junk, at least :D), and am now defragmenting.

---

