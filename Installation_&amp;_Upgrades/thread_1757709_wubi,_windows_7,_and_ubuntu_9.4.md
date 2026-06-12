---
title: "wubi, windows 7, and ubuntu 9.4"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by ashiruni on 2011-05-13
alrighty, long story short, I screwed up. I had installed a copy of ubuntu 9.1 to my sda1 partition and a copy of windows 7 to sda2 and it worked pretty well, but after needing to change the partitions around, I deleted sda1 and did a wubi install. I forgot to adjust the mbr before deleting the ubuntu install and my live CD is still running ubuntu 9.1 (think that's grub 1.5) and I can't update the live CD, as my only functioning OS is currently running off it. I suspect, therefore, that the mbr is still pointing to a now non-existant partition to find the boot files. 

So, in short, how do I use my current live CD to allow me to boot into windows in this situation?

my current partition table is sda2: windows 7/wubi, sda1: media/backups

---

### Post by bcbc on 2011-05-13
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Note: you'll get a panel after the first command with a big warning - just ignore that as it relates to using lilo for booting linux.

That will replace the bootloader. Or you can insert a windows DVD, boot to a repair prompt, and run: bootrec /fixmbr

PS if you like you can post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") so we can confirm what is going on. But the windows bootloader is what you need if you now just have Windows + wubi

---

### Post by ashiruni on 2011-05-15
Alright, that seems to have fixed it. Thanks for the advice ^.^

---

