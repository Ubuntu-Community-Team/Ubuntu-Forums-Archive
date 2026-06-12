---
title: "need help with gutsy dual boot"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by jwazzz on 2007-11-18
I tried to upgrade my dual boot with xp and feisty. I had 4 partitions xp,root, home and swap. I deleted the 3 linux partitions and was going to put ubuntu in one partition. Now nothing boots. I get a Grub error 15. When I do sudo fdisk -lu I get:
Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3ff13ff0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   196169714    98084826    7  HPFS/NTFS
/dev/sda2       196169715   235496834    19663560   83  Linux
/dev/sda3   *   235496835   239770124     2136645   83  Linux
/dev/sda4       239770125   240107489      168682+   5  Extended
/dev/sda5       239770188   240107489      168651   82  Linux swap / Solaris

I need xp for work, Im a linux noob. Please help.

---

### Post by Pumalite on 2007-11-18
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by Kadrus on 2007-11-18
Put the  Ubuntu cd in the pc...and reboot it...it tells you that it's going to enter Ubuntu Operating System..start installing..while installing..it asks you how to do you want to partition your disk..and from there you choose
Hope that helped :)

---

### Post by jwazzz on 2007-11-18
Thanks for your kind replies. I restarted gparted and deleted the partitions again. It didnt take first time.

---

