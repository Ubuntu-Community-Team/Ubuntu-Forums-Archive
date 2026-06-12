---
title: "Cant get boot loader working"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by Blackdragon1400 on 2011-10-18
I have 4 hard drives in my machine with one running Windows 7, another with a corrupted install of Windows 7 (I am just using the installed prgrams from this harddrive I cant boot from it, it crashes) And 11.10 which I installed yesterday. My 4th harddrive is just for extra space. I attached a picture of my partition table so you can see what I am dealing with.

My problem is that when installing 11.10 I apparently do not know where to install the bootloader to. It lets you choose from the root of the harddrive (listed as /dev/sda/ Western Digital etc.) or any of the partitions on it. The default is shown as the root of the harddrive so I figured I would stick with that. I tried re-installing the operating system three different times with the boot loader in the following three locations; Functional windows 7 harddrive, corrupt windows 7 harddrive and the harddive that 11.10 is installed on.

I change my bios to boot to the appropriate device and the boot loader never comes up. It just loads the windows 7 OS. 

I understand if this might be confusing hopefully the picture will help.

Ubunutu is installed at D: with / on the 15gb partition and /home on the 18gb partition (I did this for ease of upgrading later) and 2.5gb of swap.

Also, is there a way of fixing this through a live CD? It takes forever to re-install the OS just to check the bootloader.

---

### Post by garvinrick4 on 2011-10-18
Put in a Live CD (install Cd using Try Ubuntu) and open a terminal (ctrl/alt/t)
```
sudo fdisk -l
``` (lower case L)
Now pick out drive you want to install Ubuntu on.
sda
sdb
sdc
sdd
sde
and on and on.
Now when installing choose bootloader to go into same drive.
Not the partition number like sdd1 or sdd5 but always the drive as a whole like sdd.
If you installed in sdc1 parition then you choose.
sdc
to install boot loader.
After install boot into Ubuntu and:
```
sudo update-grub
```
Will add all bootable installs to config file and as menu entry on that drive for all drives.
Can boot any operating system when booting off of that drive in BIOS in other words. Must boot
off of the Ubuntu drive to get Ubuntu's grub menu.

---

### Post by Blackdragon1400 on 2011-10-18
I tried reinstalling and putting the boot loader at the location you suggested and still no-dice. I am wondering if the boot loader is getting installed incorrectly. Ubuntu looks like it installed fine to the two locations I put it "/" and "/home" but I just cant boot into it! Is there a manual way to install grub? Or perhaps make a partition at "/boot" and have it install the boot loader there?

---

### Post by garvinrick4 on 2011-10-18
> **Blackdragon1400 said:**
> I tried reinstalling and putting the boot loader at the location you suggested and still no-dice. I am wondering if the boot loader is getting installed incorrectly. Ubuntu looks like it installed fine to the two locations I put it "/" and "/home" but I just cant boot into it! Is there a manual way to install grub? Or perhaps make a partition at "/boot" and have it install the boot loader there?
You need to run this script and post it. It will put a RESULTS.txt file to post, copy and paste the whole
thing and highlight it and hit the # sign in upper right of Message box will put in nice box to read in.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
Download to Desktop and then right click on and extract and run this code.
```
sudo bash ~/Desktop/boot_info_script.sh
```

Can now tell you exactly what is going on with booting.

---

