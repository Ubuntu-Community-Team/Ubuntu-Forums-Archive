---
title: "Ubuntu lost after WinXP attempt"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by danzac64 on 2008-05-12
Dear All,
I'm new with Ubuntu. I installed Ubuntu 8.04 and I worked with it for several days. Then my son pushed me to install WinXP. I started the installation and I stopped when I realized that Win could not recognize the file system (i.e. before starting partitioning). After this attempt I could not load Ubuntu anymore! Even with Live CD, I was not able to see and mount the file system anymore.
It doesn't seem a grub issue. Fdisk doesn't see any partition. An attempt to reinstall Ubuntu with manual partitioning ended up with an empty /dev/sda device (I didn't go further and I quitted the install procedure).
How is it possible that I lost the linux file system without installing WinXP (i.e. no partitioning, no formatting)? Is there a way to recover data from the HD?
Cheers.

---

### Post by Pumalite on 2008-05-12
Boot your Live CD and from the Terminal, post:
sudo fdisk -l

---

### Post by danzac64 on 2008-05-12
I did it already... Nothing! It seems that the HD is unpartitioned and unformatted...

---

### Post by Pumalite on 2008-05-12
Copy and paste the output here.

---

### Post by danzac64 on 2008-05-12
It took a while to trasfer from Ubu to my mac... but now something appeared! Here we go.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
86 heads, 15 sectors/track, 242311 cylinders
Units = cylinders of 1290 * 512 = 660480 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      208090   134217727+   4  FAT16 <32M

Disk /dev/sda1: 137.4 GB, 137438952960 bytes
86 heads, 15 sectors/track, 208089 cylinders
Units = cylinders of 1290 * 512 = 660480 bytes
Disk identifier: 0x00000001

     Device Boot      Start         End      Blocks   Id  System
/dev/sda1p1   *           1      208090   134217727+   4  FAT16 <32M
ubuntu@ubuntu:~$

---

### Post by Pumalite on 2008-05-12
sda1 seems to be fat16. What do you want to do with your hard drives?

---

### Post by danzac64 on 2008-05-12
With that HD I just installed Ubuntu. Than I played a bit with files (e.g. I   downloaded pictures from my son's camera). Then I attempted to install WinXP but I stopped to avoid partitioning/formatting the HD...
Is it possible that the WinXP installer changed the file system before any partitioning/formatting command?

---

### Post by Pumalite on 2008-05-12
You don't seem to have any workable OS in your hard drives. Are you able to boot anything now ?

---

### Post by danzac64 on 2008-05-12
No boot from the HD. Just stucked with the HD led on.

---

### Post by Pumalite on 2008-05-12
Are they both SATA, both IDE or a mix?

---

### Post by danzac64 on 2008-05-12
It is a SATA. No IDE controllers on board.

---

### Post by Pumalite on 2008-05-12
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Make 2 partitions in your first drive. The first; at the beginning of the drive (primary)(sda1), format ntfs. The second, (at the end), format ext3. Install XP in the first partition. Install ubuntu in the 2nd going Manual and making 3 'New' partitions (delete first):
10 GB for '/'
1 GB for /swap 
The rest for /home
Press 'Forward. The installer will do the rest. Use your second drive for storage. You can format it as you wish. Ubuntu can read and write to ntfs.

---

### Post by danzac64 on 2008-05-12
No hope to recover data (at least in an easy way)?

---

### Post by Pumalite on 2008-05-12
I think your data is lost. You can try Knoppix Live CD and see if you can find something:
[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
It mounts all your drives/partitions automatically at boot.

---

### Post by danzac64 on 2008-05-12
I'll try tomorrow (now it's 1 AM in Italy). But I know I have almost no hope. Thanks!

---

### Post by Pumalite on 2008-05-12
You are welcome. Good luck.

---

