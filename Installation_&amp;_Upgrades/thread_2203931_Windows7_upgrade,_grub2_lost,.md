---
title: "Windows7 upgrade, grub2 lost,"
date: 2014-02-05
forum: Installation &amp; Upgrades
---

### Post by rodh on 2014-02-05
My Toshiba laptop was  Vista and Vista would not update and the Windows answer desk tier 2 tech upgraded me to Windows7 now I can't find Grub 2

---

### Post by oldfred on 2014-02-06
If your LInux partitions were not overwritten, you should just be able to restore grub2's boot loader to MBR.

 How to restore the Ubuntu/XP/Vista/7 bootloader 
[URL="https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader"]https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader

[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
[/URL]

---

### Post by rodh on 2014-02-06
with this live cd I can see the files from my ubuntu 10.04 install but I can't get grub----   tried to install boot repair disk via terminal but said it couldn't find the package

---

### Post by rodh on 2014-02-06
ubuntu@ubuntu:~$ boot-repair
boot-repair: command not found
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf99b3d64

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Hidden NTFS WinRE
/dev/sda2   *     3074048   194389827    95657890    7  HPFS/NTFS/exFAT
/dev/sda3       476344320   488392703     6024192    7  HPFS/NTFS/exFAT
/dev/sda4       194390014   476344319   140977153    5  Extended
/dev/sda5       194390016   464809983   135209984   83  Linux
/dev/sda6       464812032   476344319     5766144   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by oldfred on 2014-02-07
What disk were you installing Boot-Repair into? 
Your 10.04 is only still supported for server, not desktop, so any updates that are not server related will not work.

Either the full Boot-Repair ISO or a new 12.04 or 13.10 Ubuntu ISO should be used.
 LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by rodh on 2014-02-08
Thank you, I haven't had much time to do this and your last post got me past the BLOCKHEAD mode.  I was able to get the Boot-Repair disk from 12.10 and it worked just fine and I now am enjoying 10.04 on my laptop again.  Everything is still here and working properly.  I would also like to Thank Everyone involved in writing the Boot-Repair program.

---

