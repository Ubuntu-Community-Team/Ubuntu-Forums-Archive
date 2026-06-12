---
title: "help to dual boot xp and ubuntu...xp on two drives(RAID 1)"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by philohawk on 2008-04-29
I apologize if this has become redundant but after doing some research on my own, I still am not sure what I am doing. I recently  obtained a computer with three drives. The first two have XP on it already as RAID 1 and the last drive has nothing on it. My goal was to place Ubuntu on that last drive. My first attempt was to go through the normal installation process and have GRUB setup on the MBR of my first drive, but that crashed XP. Other attempts involving placing the GRUB elsewhere failed too.

Is it possible to do this? I must also say that I am new to the area of boot loaders and BIOs configurations, but I do have the overall concept of them. If anyone could give me any advice or instructions, I would really appreciate that! 

Thanks!

---

### Post by confused57 on 2008-04-29
> **philohawk said:**
> I apologize if this has become redundant but after doing some research on my own, I still am not sure what I am doing. I recently  obtained a computer with three drives. The first two have XP on it already as RAID 1 and the last drive has nothing on it. My goal was to place Ubuntu on that last drive. My first attempt was to go through the normal installation process and have GRUB setup on the MBR of my first drive, but that crashed XP. Other attempts involving placing the GRUB elsewhere failed too.

Is it possible to do this? I must also say that I am new to the area of boot loaders and BIOs configurations, but I do have the overall concept of them. If anyone could give me any advice or instructions, I would really appreciate that! 

Thanks!

You shouldn't have any problem setting up a dual boot this way.  If you haven't already, you may want to reinstall Window's IPL(Initial Program Loader) to the mbr of the first drive of your Raid...Once you're able to boot with the Window's bootloader, set your bios to boot the drive you're installing Ubuntu to as the first hard drive in the boot order before you boot the live cd to install Ubuntu.

Near the last screen of the installation process, there is an "Advanced" button in the lower right that you can click and select where to install grub.  The default is (hd0), but you might want to change this to /dev/sdc(or however the installer recognizes your Ubuntu drive).  /dev/sdc is the mbr of the drive.../dev/sdc1 would be the root partition where you shouldn't install grub in a basic Ubuntu install.

You may want to burn a Super Grub Disk, which is a great utility to have for booting issues:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

