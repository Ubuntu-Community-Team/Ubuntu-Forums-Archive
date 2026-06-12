---
title: "Advanced Format Drive Install"
date: 2016-06-04
forum: Installation &amp; Upgrades
---

### Post by spiel2 on 2016-06-04
I recently installed Ubuntu 16.04 to a western digital WD10EZEX. Its an advanced format drive. I checked the partitions and it appears to be out of alignment.

I looked around for other answers but they are all old. Recent installers should account for advanced format. I am wondering if it is a new bug and if there are any solutions.

---

### Post by oldfred on 2016-06-04
Post this:
sudo parted -l
If gpt and sda:
sudo gdisk -l /dev/sda

---

### Post by spiel2 on 2016-06-05
[ATTACH=CONFIG]269436[/ATTACH][ATTACH=CONFIG]269437[/ATTACH]

The second image is the output with fdisk.

---

### Post by oldfred on 2016-06-05
With text or terminal output please copy & paste, not screen shots. And if longer use code tags which are the # in the forum's advanced editor.

It looks ok. The extended partition is not written into, so it will not be divisible by 8. But both partitions you have are, otherwise.

If not planning on Windows often better to use gpt. And better to have smaller system partition and larger /home or /mnt/data partition.

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[URL="http://ubuntuforums.org/showthread.php?t=1768635"]http://ubuntuforums.org/showthread.php?t=1768635

[/URL]
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr) 

[URL="http://ubuntuforums.org/showthread.php?t=1768635"]
[/URL]

---

### Post by spiel2 on 2016-06-05
Thanks.

I'll look into converting to GPT.

---

