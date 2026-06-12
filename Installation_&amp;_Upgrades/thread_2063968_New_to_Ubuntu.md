---
title: "New to Ubuntu"
date: 2012-09-28
forum: Installation &amp; Upgrades
---

### Post by Saurusii on 2012-09-28
Hi all

I have just decided to try Ubuntu and there are a few things I need to know about installing it that I cannot seem to find in the documentation.

I'm currently running Windows XP SP3 on an AMD machine. I have a 500GB SATA drive that has the system and most of my data but also have a 100GB SATA drive that I have wiped clean.

I'm thinking that I should install Ubuntu on this clean drive to run alongside Windows.
The questions I have are:
1. Should I reformat the drive before installing Ubuntu on it or just let the installer do it?
2. While running Ubuntu, will I be able to access data on the larger drive, which is formatted by Windows. In particular, will I be able to open, edit and save images, documents, etc?
3. I'll obviously quickly run out of space on the smaller drive, will I later be able to create Ubuntu partitions on the other drive? Will I need to do this or will I just be able to create folders and save files on the windows disk?

Thanks in advance.

---

### Post by Speransky on 2012-09-28
1) not necessary, during installation I'll be able to partition your disk;
2) Yes, Ubuntu have access to ntfs(it will be shown in file manager as external storage (like usb flash drive)); 
3) Later you can create Ubuntu partition (EXT4) or proceed to use ntfs.

There is one more subtlety. When you are installing ubuntu, in dialog with manual dividing up the disk (it's prefer way) you may choose in what device to install bootloader. So if you want to use GRUB menu to choose OS for booting, you need to set device with Windows install (often it is /dev/sda), but if you want to choose from bios, you need to set device with ubuntu install (it will be /dev/sdb)

---

### Post by agillator on 2012-09-28
1. During the installation you will be asked where you want to install Ubuntu. During that step you will tell the installer to format for Ubuntu, so you need do nothing special before installing. If you were to want to install on the other drive beside Windows, which you could do, you would be wise to make room first by resizing partitions.

2. Linux can read (and write) Windows partitions. Windows will not recognize and read/write Linux partitions so those partitions you wish to access from both systems will need to be one of the Windows file systems.  

3. Unless you are saving a bunch of movies or other files that are gigabytes big I think you will be pleasantly surprised at how long it will take you to fill 100GB. However, eventually you probably will. What you do at that time is up to you. You can use Windows' partitions or you can resize to create space and create new Linux partitions. Unless it is something you need to access from both systems, though, you will probably want to use one of the Linux file systems. One reason will be the difference in handling permissions. You will also find that Linux file systems do not get fragmented. As you work with Linux, become familiar with gparted. It is your friend. It is, however, very powerful which means it is also very dangerous and you can screw things up very badly very easily.

---

### Post by Saurusii on 2012-09-28
Thanks guys!!

---

