---
title: "Dual boot ubuntu 7.10 with a partition copy of windows XP"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by guggikofod on 2008-03-18
(I am completely new to most of the below! please explain it as if to a 4 year old)

I wanted to change my windows XP system to a dual boot system, and to exchange my harddrive, on a laptop machine (only cd-rom)

so, I got an external HD (USB), and a new HD. I prepared the systemrescueCD and the Ubuntu 7.10 cd.

 first I cleaned up my old win XP (removed programmes, defragged), eveything working fine. using gparted, I copied this partition (20Gb) to the external HD. I then replaced the old HD for the new, and used gparted to partition the new HD:

/devsda1    ext3               502 Mb
/devsda2    ntfs                19.54 Gb   (flag: boot)
/devsda3    extended       128.83 Gb
  /devsda5    ext3             39.06 Gb
  /devsda5    swap          1004.03 Mb
  /devsda5    ntfs             88.70 Gb

then reboot, inserting now the ubuntu cd, and installing ubuntu (manual selection of the partitions). ubuntu installed beautifully.

I then copied the windows partition from the external HD to the ntfs partition, using gparted.

restarting the machine. at this point the machine loaded directly into ubuntu, not giving the choice to boot XP. I therefore edited menu.lst to show the XP boot option, which worked as it should. however, when booting the XP partition, I got the message:

Windows could not start because the following file is missing or corrupt:
<Windows root>\system32\hal.dll

it said on [http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm) that this issue is probably due to a flawed boot.ini, which would make sense, however the solution requires low-level XP hacking using Windows Recovery tools, and I am afraid that this will screw up more than it will fix. 

where to go from here?

thx

---

### Post by Pumalite on 2008-03-18
I'm not a Windows user, but I think your Installation CD comes with a Repair Filesystem option.(I might be wrong)
Besides, you can boot XP with Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by guggikofod on 2008-03-18
thanks for the link to super grub. unfortunately, it seems to be deeper than what super grub can fix. i used super grub to load my win partition, but it resulted in exactly the same response as before (missing hal.dll). I don't think the file system itself is corrupt, I think the problem is with the boot.ini file, but I have no idea how to write it  properly

---

### Post by guggikofod on 2008-03-18
i made one more step. i mounted the windows disk, and edited the boot.ini file:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional" /fastdetect

instead of 1's I wrote 2's

I could now restart, grub boot into win XP. unfortunately, the first XP boot cycle escaped to ubuntu somehow? in ubuntu, I couldn't mount and look at the win partition. however, restarting and grubbing into win XP actually caused it to work properly. amazing.

---

### Post by Pumalite on 2008-03-18
Congrats.

---

