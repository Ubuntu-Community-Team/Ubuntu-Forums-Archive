---
title: "Ubuntu Server installation problem with mixed PATA and SATA driver"
date: 2008-08-22
forum: Installation &amp; Upgrades
---

### Post by kikiriki on 2008-08-22
Hi,

this is my first post, I am a complete Linux beginner.

I am trying to build a home server using the following hardware:
- Asus motherboard with 690V chipset
- Athlon LE-1620 processor
- 1 GB RAM
- 40 GB PATA disk for the OS installation
- 3 SATA hard disks 750 GB for data in a RAID 5 configuration

I tried Ubuntu server and alternate editions versions 8.04 and 8.04.1 for x86 and also 64 bit versions. I could not find a way to install Ubuntu server and RAID.

All hard disks are clean; all partitions deleted using Ranish partition manager. I do not want to install anything complicated, no multi-boot or something similar.

The first attempt was to connect only PATA hard disk, install Ubuntu server and reconnect SATA drives and install RAID array. I manually created new partitions, set RAID autodetect; after formatting all SATA disks I installed mdadm. This didn’t work because mdadm could only start 2 out of 3 hard disks and could not create configuration files. I used this guide to create RAID [http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188)

The second attempt was to connect all drives and use manual partitioning. Everything seemed to work fine; however, after rebooting GRUB reported error 17 and could not start operating system.

It seems that the error is related to the way installer and GRUB detects hard disks. I tried to modify menu.lst file and it is read only and impossible to modify.

The other interesting thing is that the small PATA drive is not recognized as /dev/hdx it becomes /dev/sdd when all drives are connected before installing.

I saw many threads about GRUB and mixed PATA and SATA hard disk problems; however it is always about dual-booting, multiple Linux or Windows systems. Nothing similar to this problem. I am trying to install Ubuntu server on a typical home server.

Thanks

---

### Post by spiderbatdad on 2008-08-22
Have you tried installing or fixing grub, as according to this post:[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

There was also an option on my live cd to repair grub...post installation. I would have to look for the option. I believe I accessed it several steps into the installation process...after actually installing and reinserting the live cd, or it may be through a repair option on the start up screen.

---

### Post by kikiriki on 2008-08-25
Thanks for a quick response. I searched this topic a lot on the Internet. It seems to be related to SB600 Southbridge chip and BIOS settings for SATA disks: Native IDE, RAID or AHCI. I will experiment with different options and let you know if it helps.

Do you know how to detect hard disk problems, how to change configuration files like: device.map, menu.lst or fstab. When I try to edit menu.lst with vim I cannot save changes because file is read-only. Any ideas why?

I will try to reinstall GRUB after experimenting more with SATA BIOS options. At this point it seems useless because I have a hard disk detection problem; hard disks are detected differently during Ubuntu installation and GRUB installation. I don't know how to fix that. During booting I see that GRUB is trying to boot from hd(3,0). If I change that to hd(0,0) than it starts. However, making a permanent change in menu.lst is not possible because I cannot save that file, it is read-only.

---

### Post by spiderbatdad on 2008-08-25
> **kikiriki said:**
> Thanks for a quick response. I searched this topic a lot on the Internet. It seems to be related to SB600 Southbridge chip and BIOS settings for SATA disks: Native IDE, RAID or AHCI. I will experiment with different options and let you know if it helps.

Do you know how to detect hard disk problems, how to change configuration files like: device.map, menu.lst or fstab. When I try to edit menu.lst with vim I cannot save changes because file is read-only. Any ideas why?

I will try to reinstall GRUB after experimenting more with SATA BIOS options. At this point it seems useless because I have a hard disk detection problem; hard disks are detected differently during Ubuntu installation and GRUB installation. I don't know how to fix that. During booting I see that GRUB is trying to boot from hd(3,0). If I change that to hd(0,0) than it starts. However, making a permanent change in menu.lst is not possible because I cannot save that file, it is read-only.

The root file system is read only for security. You will need "sudo" in front of any commands to edit those files, or gain a root shell with "sudo -i"

---

### Post by kikiriki on 2008-08-28
I did another attempt to install Ubuntu server. In order to prepare hard disks I used UBCD4Win to delete beginning of each hard disk including MBR and partition tables.
Installation was successful no errors reported. RAID array was recognized and MD0 was listed with 1.5 TB.
However, after rebooting, system could not boot. After booting from the installation CD into the Rescue option device.map file contained following entries:
hd0 - sda
hd1 - sdb
hd2 - sdc
hd3 - sdd
Knowing that SATA drives are sda, sdb and sdc it is clear that detection didn't work properly. I tried re-installing GRUB option and selected hd(3,0) that correspond with sdd1 partition. After fixing also boot flag (it was set on sda instead of sdd) I did a reboot.
I only got to the GRUB second stage error 17. After manually setting in GRUB to boot from hd(0,0) Ubuntu finally started. However, during start-up I noticed that RAID reported an error, something like RAID array is not clean. It is clear that Ubuntu installer also selected /dev/sda1 to install.
Did I somehow missed an option during installation to select where to install Ubuntu?

---

### Post by kikiriki on 2008-09-01
A few long days, a lot of Internet surfing and countless installations.

I failed to install Ubuntu server 8.04 on my computer using the installation CD image. I tried numerous options like pci=nomsi, irqpoll, etc. I also updated motherboard BIOS. Hard disk detection did not work properly. My first SATA disk was always recognized as a boot disk, when in fact it should be my IDE disk.

Than I saw a post where somebody installed Ubuntu 7.10 and upgraded to the latest version afterward; I decided to give it a try.

Ubuntu server 7.10 x86 version detected my hard disks properly without any intervention. However, it could not detect my on-board network card. Probably because it is on the PCI-E bus, not on the PCI bus.

Luckily I had some old network 10/100 MBit card. It was detected properly and I installed Ubuntu server 7.10, alas without software RAID5 because during installation Ubuntu detected that my disks were previously formatted for RAID. However, md0 device had one disk damaged.

I had to manually delete superblocks on all hard disks using this post: [http://ubuntuforums.org/showthread.php?t=884556](http://ubuntuforums.org/showthread.php?t=884556) and create software RAID from scratch. After a few hours of syncing my RAID array was created and working fine. I created mounting point and updated fstab.

The last step was to update to 8.04 using the following commands:
sudo apt-get update
sudo apt-get upgrade
do-release-upgrade

It was easy to remove the old network card and activate the on-board network controller with some tweaking in /etc/network/interfaces.

I admit that I could not find a solution. However, this workaround is good enough for now. I hope that the next release will not have such a serious installation issues.

There are still some small issues with the system. I am not sure if the mdadm.conf file has all sections filled in properly. I suspect that the line "spares=1" should be deleted. It will take a few more days to polish the system.

---

