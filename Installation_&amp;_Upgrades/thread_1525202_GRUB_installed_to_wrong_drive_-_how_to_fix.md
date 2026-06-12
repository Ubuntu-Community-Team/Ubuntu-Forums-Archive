---
title: "GRUB installed to wrong drive - how to fix ?"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by fritzm on 2010-07-06
I have a system with two hard drives: an old one with XP and Ubuntu on it, and a new one on which I have done a fresh install of XP. The BIOS is set to boot off the new drive.
I have now installed Ubuntu Studio 10.04(off an alternate install disc, not a live CD)onto a partition on the new drive. The installation went fine, but it appears to have written the GRUB bootloader to the old disc. The result is that when I boot up, the system boots straight into XP off the new drive, without ever seeing GRUB. I could reset the boot order in the BIOS each time I boot according to which OS I want, but that is cumbersome; also I would like to be able to remove the old drive at some point.

What is the easiest way for me to re-install GRUB to the new disc ?

Fritz

---

### Post by shakthi_gs87 on 2010-07-06
I guess, you can permanently set the BOIS to boot your old disk.
     Other alternative is using grub-install   Let me detail the operation.... 
  Use mount to identify the name of your root device 
  example:
 $mount


 /dev/sdb7 on / type ext4 (rw,errors=remount-ro)
 /dev/sdb8 on /boot type ext3 (rw)

 So root device  on my system /dev/sdb7
 also note that I have separate boot partition /dev/sdb8

 $grub-install --root-directory=/boot /dev/sdb 

    Installs grub on /dev/sdb  (disk that contain Ubuntu) 
   If I am not having separate boot partition then

 $grub-install  /dev/sdb

 will work

---

### Post by oldfred on 2010-07-06
reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
Then:
sudo update-grub

So it remembers where to reinstall grub:
sudo dpkg-reconfigure grub-pc
spacebar to choose drive, enter to accept, do not choose partitions

But if you remove sda you may want to run the dpkg command  so it reinstalls to sda as it will save the install to sdb even after it becomes sda.

---

### Post by fritzm on 2010-07-07
Thanks for the replies; I seem to have fixed it by using the repair option from the installation CD and telling it to use sdb for GRUB installation.

Fritz

---

