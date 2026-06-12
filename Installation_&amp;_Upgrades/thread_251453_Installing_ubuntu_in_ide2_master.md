---
title: "Installing ubuntu in ide2 master"
date: 2006-09-05
forum: Installation &amp; Upgrades
---

### Post by mbc28 on 2006-09-05
Hello, I'm novice in linux. I installed ubuntu in a partition in the same hard disk as windows xp, ubuntu works ok, but I had many problems with grub and windows, and finally I had to format entire hard disk. Now I want to install ubuntu again and I want to know if I can install it on a hard disk that is on IDE2 master and if it is possible, where grub will be installed, in the MBR of IDE1 master HDD (windows xp) or in the MBR of IDE2 master HDD (Linux)? 

Thank you!

---

### Post by lha on 2006-09-05
Hi mbc28,

Take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=124989"). I believe you will find it useful. You are probably interested in the first and the second post. The first post describes a problem similar to yours and the second one presents a good solution to it.

---

### Post by donkey42 on 2006-09-05
i'm also a linux noob,but, i personally would install each OS one at a time (disconnect other HDD) connect each HDD as primary master, install your chosen OS, then put one HDD as primary master and the other HDD as secondary master, then select the bootable drive in the BIOS, i dont know hoe to do it with grub or lilo yet, i know it is possible but i don't know how to do it yet

---

### Post by lha on 2006-09-05
> **donkey42 said:**
> i'm also a linux noob,but, i personally would install each OS one at a time (disconnect other HDD) connect each HDD as primary master, install your chosen OS, then put one HDD as primary master and the other HDD as secondary master, then select the bootable drive in the BIOS, i dont know hoe to do it with grub or lilo yet, i know it is possible but i don't know how to do it yet

Well, maybe you too should read the [thread]("http://ubuntuforums.org/showthread.php?t=124989") I mentioned. :) There's no need to fool around with bios settings.

---

### Post by bkizzle on 2006-09-05
Hmm, well I have my setup as XP on the master drive and ubuntu on the slave. Didnt have to make any config. changes what so ever. Everything seems to be working fine, and before boot i get to choose which OS i want to roll with.

---

### Post by mbc28 on 2006-09-06
Thanks to all, but I still don't know where GRUB will be installed, on IDE1 HDD or IDE2 HDD. I prefer in the IDE2 HDD (linux) because I had some problems with Grub and Windows at first time I installed Ubuntu.

Thanks!

---

