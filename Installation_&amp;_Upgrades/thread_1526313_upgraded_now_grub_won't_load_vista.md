---
title: "upgraded now grub won't load vista"
date: 2010-07-07
forum: Installation &amp; Upgrades
---

### Post by jimbou1981 on 2010-07-07
Several months back I installed Ubuntu on my system that I already had Windows Vista on. I believe I used a program called partition magic to install linux. That all work just fine, I don't use ubuntu on a regular basis, I had it just in case windows had a problem. I decided to update from 9.10 to 10.04 and now I can't get Windows Vista to load. At the grub menu when I select Windows the screen just goes back to the grub screen. 

sudo fdisk -l

james@james-laptop:~$ sudo fdisk -l
[sudo] password for james: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf99b3d64

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       27269   217496782    7  HPFS/NTFS
/dev/sda3           27270       30401    25157790    5  Extended
/dev/sda5           27270       30266    24073371   83  Linux
/dev/sda6           30267       30401     1084356   82  Linux swap / Solaris
james@james-laptop:~$ 

please does any one knows what needs to be done, I think I may have installed grub on my windows partition during the upgrade, but I don't know for sure.

---

### Post by lindsay7 on 2010-07-07
Thy this.


[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

---

### Post by jimbou1981 on 2010-07-07
Thanks, but while you were posting this I found a different way to get back to vista. It included using a vista boot dvd and selecting command prompt and entering:
 bootrec.exe /fixboot
 bootrec.exe /fixmbr then restarting and vista loaded with no problem. However I no longer have access to Grub or ubuntu. So what would I do from here to get grub and ubuntu back? Would I just use a ubuntu boot dvd?

---

### Post by oldfred on 2010-07-07
lindsay7 link will work.

Or 
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Install from LiveCD:
Find linux partition change sda5 if not correct or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

