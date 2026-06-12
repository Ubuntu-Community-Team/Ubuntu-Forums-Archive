---
title: "Dual Boot - Upgrade to Windows7"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by cmcesq on 2010-01-30
I presently have a dual-boot configuration where WinXP is on one hard drive (the primary) and Ubuntu is on another (the slave).  GRUB 2 handles the dual boot.  

I'm thinking of upgrading WinXP to Win7 which -- from what I understand -- will format the Windows drive and do a fresh install of Windows 7. 

I'm assuming this will wipe out the Master Boot Record and thus screw-up my dual boot; which will then require a reinstall of Ubuntu onto the other hard drive.  

I've backed-up the MBR using MBRFix, but I'm assuming I won't be able to simply restore the old MBR (on the WinXP drive) after upgrading to Win7.

So, to get to the question (finally), is there anyway to upgrade the WinXP hard drive and still maintain the GRUB dual-boot functionality without having to re-install Ubuntu also?

Many thanks in advance.

---

### Post by e-Gee on 2010-01-30
Yes but after instaling windows you will have to boot from ubuntu live cd go to terminal and type :

sudo fdisk -l

sudo mount /dev/sda1 /mnt

sudo grub-install -&#8211;root-directory=/mnt/ /dev/sda

restart computer and boot in to ubuntu and in terminal type :

sudo update-grub

That is it

---

### Post by presence1960 on 2010-01-30
> **e-Gee said:**
> Yes but after instaling windows you will have to boot from ubuntu live cd go to terminal and type :

sudo fdisk -l

sudo mount /dev/sda1 /mnt

sudo grub-install -&#8211;root-directory=/mnt/ /dev/sda

restart computer and boot in to ubuntu and in terminal type :

sudo update-grub

That is it

e-Gee is correct, but I want to elaborate on those commands so you understand what you are doing. After installing windows reboot your machine once or twice to make sure windows does indeed boot properly. If it does boot correctly  boot off the Ubuntu 9.10 Live CD & choose "try ubuntu without any changes", when the desktop loads if you don't know which partition ubuntu is on open a terminal & run ```
sudo fdisk -l
```
That is a lowercase L in -l
Locate your ubuntu partition. Note it (sdbX)

Next in terminal run ```
sudo mount /dev/sdbX /mnt
```
Where X = the # of the partition on sdb, i.e. sdb1, sdb2, sdb3, etc. This will mount your ubuntu partition.

Next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```
This will put GRUB back on your primary partition that boots first in BIOS.

Note: you said your ubuntu is on the slave disk so your ubuntu partition will be sdbX as the slave is sdb and the primary is sda.

For the community documentation on GRUB2 see [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
Use the links on right to find the page for reinstalling GRUB2 (#11)

---

