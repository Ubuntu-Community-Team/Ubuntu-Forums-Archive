---
title: "Replace Windows 7 with Ubuntu 11.04 from Dual Boot"
date: 2011-08-04
forum: Installation &amp; Upgrades
---

### Post by oogway on 2011-08-04
I currently have a dual boot system with BackTrack 5 and Windows 7. I no longer want Windows 7, so I wish to replace it with Ubuntu 11.04. What's the best way to remove the Windows partition and install ubuntu in it without screwing my grub loader (having it updated with Backtrack 5 and Ubuntu 11.04)?

---

### Post by Hakunka-Matata on 2011-08-05
Booting to a Ubuntu liveCD and using Ubuntu's partition editor would be a good way to start.  You can delete your windows7 partitions there and create the necessary partitions for your ubuntu installation.

Installing Ubuntu will also install Grub (Ubuntu's bootloader) and that will allow you to select which system to start.

---

### Post by Basher101 on 2011-08-05
Depending on how big your Windows partition is, you can get the "install aside" option when you try to install from the LiveCD if you got enough space after deleting Windows

---

### Post by Furball588 on 2011-08-05
Do you have a preference on how you want to deal with grub from backtrack?

I guess I'm just not seeing any reason to let backtrack control things if you don't have any preference here.

---

### Post by oogway on 2011-08-05
Well, I would still want the OS selector via grub, having Ubuntu 11.04 as the main OS. Backtrack can be left down as a secondary option (if this is possible, don't really care who manages my boot, Ubuntu or Backtrack). 
 
Should I delete the windows system and boot partitions completely with the Ubuntu LiveCD? I just don't want to screw my Backtrack OS since it's now stable after several weeks scratching my head!!!

---

### Post by Furball588 on 2011-08-05
What's your partitioning look like now?

I believe that backtrack also uses grub2.  If that's the case, then the ubuntu install should take care of everything.  At worst, you can mount the boot partition in backtrack and add the entries into the 11.04 side of things manually

IIRC, if you tell the installer in 11.04 not to install on the MBR, the grub files are still generated, so working the other way would work as well.

---

### Post by oogway on 2011-08-05
These are my partitions right now:

root@bt:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b278a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       42517   341412245+   7  HPFS/NTFS
/dev/sda3           42517       60802   146869249    5  Extended
/dev/sda5           54690       60802    49092608    7  HPFS/NTFS
/dev/sda6           42517       54189    93754368   83  Linux
/dev/sda7           54189       54690     4018176   82  Linux swap / Solaris

Partition table entries are not in disk order
root@bt:~# fdisk -l | grep NTFS | awk '{print $1}'
/dev/sda1
/dev/sda2
/dev/sda5

Not sure if that helps. If not, I will just proceed with the Ubuntu LiveCD and cross fingers lol :D

---

### Post by oogway on 2011-08-07
Everything worked as expected. I used the partition manager from the liveCD to delete NTFS system and boot drives. Installed on the newly free partition and good to go!! Backtrack and Ubuntu working great! Thanks guys!:guitar:

---

### Post by Hakunka-Matata on 2011-08-07
Hey, good to see it's all fixed up. Use **_[COLOR=Red]Thread Tools[/COLOR]_**[COLOR=Black] to mark your thread solved.[/COLOR]

---

