---
title: "dual boot partitioning"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by Rusty on 2007-10-23
I have just downloaded the Ubuntu 7.10 installation CD and started the installation. I currently have a setup with dual-boot between Windows XP and Archlinux, but I want to earse the Archlinux partitions and have a dual-boot setup between Ubuntu and Windows XP. The problem is that Ubuntu does not recognize any partitions on my hard drive so the only option it gives me is to format the whole disk which is not an option. What could I do to get Ubuntu to recognize my partitions?

The partitions are formated as NTFS on a SATA disk. I tried in GParted on the live CD too, but I guess it is the same backend or something, because it had the same result. When I installed Archlinux I did not have any similar problems, what should I do?

Anders

---

### Post by hal8000 on 2007-10-23
> **Rusty said:**
> I have just downloaded the Ubuntu 7.10 installation CD and started the installation. I currently have a setup with dual-boot between Windows XP and Archlinux, but I want to earse the Archlinux partitions and have a dual-boot setup between Ubuntu and Windows XP. The problem is that Ubuntu does not recognize any partitions on my hard drive so the only option it gives me is to format the whole disk which is not an option. What could I do to get Ubuntu to recognize my partitions?

The partitions are formated as NTFS on a SATA disk. I tried in GParted on the live CD too, but I guess it is the same backend or something, because it had the same result. When I installed Archlinux I did not have any similar problems, what should I do?

Anders


That is very odd. I believe the gparted in Ubuntu has been updated and recognises more file systems,
the problem occurs when you have FreeBSD and Solaris partitions or other partitions that gparted does not like.
Do you have any other live linux distros, knoppix for example? If yes you can use knoppix as a live CD and from the linux terminal use fdisk to erase the partitions.
As you have a SATA drive the partitions will be sdax where x is the partition number. Another method may be to use  windows acronis to delete the partitions.

What I have noticed is that certain distributions, notably Fedora 7, Saybon 3.4e  recognise my hard drive as scsi, maybe its scsi emulation, but as I have 23 partitions, Fedora gives mea message
warnings partitions about sda15 will not be recognised!??  This was not the case with Fedora 5 so Feora is deleted now and i run Pardus Linux in its place.

As you only have archlinux installed, then I ecpect you will have a /, /home and /swap partion at least plus a ntfs for windows.

During installation of Gutsy, I got the same message to use the full hard drive but also a custom partition, this time I hid the solaris (bf) and freebsd (a5) partitions by changing their type to 83 with linux fdisk.
I hope you get some more suggestions to fix this, their may even be some more windows partition software that can alter the partitions, I dont know of anything except acronis partition manager.

---

