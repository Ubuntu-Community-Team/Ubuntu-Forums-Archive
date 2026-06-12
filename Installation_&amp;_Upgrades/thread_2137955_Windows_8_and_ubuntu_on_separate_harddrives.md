---
title: "Windows 8 and ubuntu on separate harddrives"
date: 2013-04-22
forum: Installation &amp; Upgrades
---

### Post by gmg2000 on 2013-04-22
Hello ubuntu forums,

I thinking about building a new desktop. Conventional wisdom suggests that put both operating systems on one drive,
and use the other drive for storage. My family isn't computer savvy and the grub screen would confuse them. What I was
thinking about was this:Install Windows 8 and Ubuntu on separate drives. Create a usb installion of ubuntu. Use the usb to boot
into the second drive when needed. Well this work?

I have several usb installions of linux, but I've found that they slow down and pause over time. That is why I want a dedicated ubuntu
harddrive.

Thank you in advance.

---

### Post by Cheesemill on 2013-04-22
You could always just hide the grub screen altogether and set Windows as the default boot.

This way Windows would always boot unless you hit the shift key to show the grub menu.

---

### Post by oldfred on 2013-04-22
If you have two drives you have two MBR. You can set BIOS to boot Windows drive and when you want to boot Ubuntu use f12 or whatever is one time boot key to boot Ubuntu. You can put grub on a flash drive and boot from that but with two drives you do not need to. There were just in the last couple of days two thread where they had Ubuntu on same drive and wanted to boot Ubuntu from flash drive.

If your Windows 8 is pre-installed and is then UEFI with secure boot, it is a bit more difficult, but similar. It is best to install both systems with gpt partitioning on drives and in UEFI mode. Then one time boot key will still give UEFI boot options.

With either install you can set grub menu to 3 seconds and default to Windows, so everyone else barely sees menu, if you want as another alternative.

With a second drive you do have to use Something Else or manual install to get the option on which drive's MBR to install the grub2 boot loader into.
 Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

---

### Post by sudodus on 2013-04-22
Yes, you can make it work like that.

But I would recommend that you make sure to get a mobo with a couple of USB3 ports. Then booting from a USB3 pendrive, HDD or SSD will be quite fast and nice. Today Sandisk Extreme are good USB3 pendrives, but the market is changing quickly, so you should browse the internet for up to date information about performance and price of the USB3 devices.

If Windows is installed with UEFI, you need to run Ubuntu in UEFI too, so use Ubuntu 64-bit version 12.04.2 or newer. Otherwise you must switch the UEFI setting on and off when you switch between Windows and Ubuntu.

---

### Post by gmg2000 on 2013-04-24
Okay, thanks for all the suggestions. Follow up question:With this setup, would it be possible for a mechanical drive for storage? Ideally, I want the Windows OS and Ubuntu OS 
on SSDs. Would the Windows OS recognize the storage drive?

---

### Post by oldfred on 2013-04-24
Yes, you just have to use NTFS format if you want to share data with Windows. I have both a NTFS data partition from when I still booted XP and a LInux formatted partition for all new data now that I am not using XP. My data is on sdc hard drive and my sdd is my SDD. I have some data on sda, & sdb which are my old small 160GB drives.

I have two Ubuntu installs in my 64GB SSD including /home, but am agressive about moving data and even some hidden folders with more data like Firefox profile to my data partitions. I share my Firefox & Thunderbird profiles with all my installs including XP.

---

### Post by gmg2000 on 2013-04-26
Sorry for the late response. Thank you.

---

