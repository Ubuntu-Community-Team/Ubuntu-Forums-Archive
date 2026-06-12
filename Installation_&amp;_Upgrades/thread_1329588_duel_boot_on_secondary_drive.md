---
title: "duel boot on secondary drive"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by techforay on 2009-11-17
I would like to duel boot upuntu with windows.  My primary drive is pretty full but i have another that is huge.  Is it acceptable to load ubuntu on a drive other than that primary drive. If that is possible do you have to designate the whole drive to ubuntu?

---

### Post by darkod on 2009-11-17
Yes, you can install it on a second drive. And you do NOT have to dedicate the whole drive for it.
Just make a plan how much of the second drive you need/want for ubuntu, and you can have the rest as ntfs partition for example, that both windows and ubuntu can read. Greate way for shared extra space.

PS. Some people would say to install the grub2 bootloader on the second drive too. Personally, since your pc is already set up to boot from the first drive (I assume), I think it's better to let grub2 install there, over the windows bootloader. When installing ubuntu and you get to the last screen before clicking Install, there is button Advanced which will offer you choice where to install grub2. I've seen plenty of people report problems sometimes even unaware that they left grub2 to go on the second drive and the pc is still booting windows directly because it's looking for bootloader on the first drive first. With multiple drives you have to make up your mind, make your choice, and act accordingly. You can put grub2 on the second drive too, but then you need to instruct BIOS to search for boot on that drive first.

---

### Post by blueridgedog on 2009-11-17
The current install may put the boot loader on the second drive (versus the first) and if that is the case you may need to tell your system bios to boot off of the second drive (which should also boot windows), or install the grub boot loader onto the first drive.  If you go down that path and need help, you can create a new thread.

---

### Post by audiomick on 2009-11-17
btw. duel is when two people fight, actually duell. You mean dual. It is an iteresting thought though, a duell boot. Ubuntu vs. Windows....;)

---

### Post by darkod on 2009-11-17
If it wasn't only for one single app that simply can't work in wine, the duel would be long over. :)

PS. The automatic spellchecker seems to think duel is correct and duell not.

---

### Post by techforay on 2009-11-17
According to a Ubuntu pocket guide that I am reading the option exist to install Ubuntu within Windows (Wubi)
"Wubi allows Ubuntu to be installed inside Windows as a series of virtual
hard disk files. It is perhaps the simplest and most fuss-free method of
installing Ubuntu."  Will this method automaticly select where the grub boot loader is put and is there any other considerations like performance. I am a rookie and intend to understand much more about linux applications than I do now but that will be a process.

---

