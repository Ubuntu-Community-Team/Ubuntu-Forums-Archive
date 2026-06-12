---
title: "Hard Drives not recognized"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by Sergeant_BoB on 2009-12-22
Hi,

I searched the internets for a solution but i didnt find any. So i hope you guys could help me.
My setup is 
Q6600
4GB ram
3870 Nvidia
200GB WD
250GB maxtor
500GB WD

And my problem is that when insert my cd and want to install. it does not recognized my hard disks. Well it does recognize the maxtor, but i want to install it on the 500 GB WD.
I've unplugged all the others and just the 500GB in it and nothing new.
I can see it in the live CD though so i dont know whats wrong ?
I've got 2 partitions on it 100GB for the ubuntu (unaccolated) and the rest is NTFS with data. 
in the terminal it shows this:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b4d73c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           12749       60801   385985722+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 

can u guys help me ? :o
thanks alot !

Sergeant_BoB

---

### Post by darkod on 2009-12-22
If you are not using raid, while booted with the cd like this, in terminal execute:
sudo apt-get remove dmraid

See if that helps.

---

### Post by mxc1090 on 2009-12-22
Search a wee bit harder next time [http://ubuntuforums.org/showthread.php?t=1311512&page=3](http://ubuntuforums.org/showthread.php?t=1311512&page=3)

First thing on google for "ubuntu 9.10 does not detect hard drives"

---

### Post by Sergeant_BoB on 2009-12-23
ah i always typed 'recognize' in google i should stop the fancy words :D

ill try that later today!

---

