---
title: "Trouble installing Ubuntu on APM partitioned harddisk (Mac G4)"
date: 2013-01-29
forum: Installation &amp; Upgrades
---

### Post by aurora72 on 2013-01-29
Hello

I'm trying to install Ubuntu 10.10 PPC on a Mac mini G4 (PowerPC) 

It will be one of the 3 OS'es on the harddisk, the other 2 are: FreeBSD 8.2 PPC and Leopard.

To make such a "triple-boot" machine, I've partitioned the harddisk from scratch using "gpart" in FreeBSD PPC (Live CD) It's roughly like that:

1st partition: APM (Apple Partition Map) (8.7KB)
2nd partition: Apple-boot code (contains boot code necessary for FreeBSD PPC) (1MB)
3rd-8th partitions: FreeBSD-ufs (6 main partitions necessary for FreeBSD) (about 10GB)
9th partition: Ext4 --> This is the partition I want to install Ubuntu on (4.3GB)
10th partition : Swap Space --> This will be used by Ubuntu (1.1GB)
11th- rest of the harddisk: HFS+ (installed Leopard; it successfully boots and works)

gpart cannot do Ext3 or HFS+ formats. I've done the HFS+ formattin using Disk Utility of Leopard Install DVD and done the Ext3 formatting using the Disk Utiliy of Ubuntu 10.10.

The basic problem is Ubuntu 10.10 Install cannot see the 9th partition during the "Specify the Partitions Manually (advanced)" section (I've translated this from my native language, may not be the exact word). Instead, it detects/sees the disk as a single disk as the /dev/hda device.

To shed some light onto the problem, I'd like to state that GParted Partition Editor in Ubuntu>>System>>Administration has exactly the same problem of treating the disk (which was partitioned by gpart) as a single disk/partition. It displays it just as "unallocated and the File System again as "unallocated"

This is not the case with the Ubuntu's Disk Untility. It detects/sees all the partitions as it should. That was not a problem with the Leopard's DU either. I was able to install Leopard into the desired partition anyway.

How can I overcome this problem? Is there a way to make Ubuntu Install see the partitions correctly and if it's possible to install Ubuntu on that partition?

Thanks.

Note: I had no problems installing FreeBSD and Mac OS X as a dual-boot system. I guess that's because Mac OS X's Disk Utility can detect/see the FreeBSD partitions (and all other partitions made by gpart) without requiring any action. So that I can install OS X into any partition I like, after I have installed FreeBSD. In Open Firmware 's graphical boot screen (alt key pressed) both OS'es appear, too.

---

### Post by aurora72 on 2013-03-06
Answer to my own post: Any harddisk partition, created or ***modified*** by gpart cannot be detected by GParted (or Ubuntu Installer for the same matter)

That is, to create a dual-boot system of FreeBSD PPC and Ubuntu PPC, the partitions should never be modified by gpart until Ubuntu once gets installed.

This is verified by my own several trials and errors.

---

