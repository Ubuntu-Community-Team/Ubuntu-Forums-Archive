---
title: "Dual Boot Questions - Stuck in XP - Aaargh!"
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by richardq on 2006-07-04
I've currently got 2-160GB hard drives (one sda, one hdb) partitioned as follows:

sda:
sda1 = 108GB NTFS partition with XP Home on it (this is the boot drive c: )
remainder is unused

hdb:
hdb1 = 100GB NTFS partition used as my XP data drive
remainder is unused


I previously had Breezy (dist-upgraded to Dapper) on it which I've since removed. I was using NTLOADR to boot grub at the time. I've downloaded the dapper-desktop and dapper-alternate ISO's and put them on CD's and I want to do a fresh Dapper install but I'm having problems and have a few questions:

1. The system is still giving me a choice to boot Linux or XP-Home when I start the machine. Should I re-edit the boot.ini file to remove this choice and delete the LINUX.LNX file I previously created before installing Dapper?

2. What is the best way to setup partitions for the new linux install. I previously set up my root, swap and boot parititons on the same drive (sda) as my windows boot drive and had my /home partition on the hdb drive. I'm still unclear as to which partitions I really need to set up. For instance I've read on these forums that the /boot partition is not really required.

3. Is it easier to just create all the dapper partitions on the sda drive to make the install easier?

4. I've read that the Dapper installer recognizes the windows file system and will install grub accordingly, but when I've rebooted from the install, Grub just hangs. I'm not sure if Question 1 has anything to do with it. I've booted the live CD after the install and created a new LINUX.LNX file and put it on my C:\ drive but this hasn't helped.

5. My bios doesn't allow me to boot from the slave drive and I don't have a floppy drive at all so most of the dual-boot solutions I've read about don't seem to apply to my situation.

---

### Post by FenrisAbraxas on 2006-07-04
Well AFAIK it's enough that GRUB is installed in the MBR hda (Master Disk) then you can boot Linux in any partition it doesn't care if it's master or slave.

Or you can use the partitioner to resize your windows partition (in your first disk) but resizing is always dangerous and you should make a backup of your data. :D

---

### Post by richardq on 2006-07-04
[QUOTE=FenrisAbraxas]Well AFAIK it's enough that GRUB is installed in the MBR hda (Master Disk) then you can boot Linux in any partition it doesn't care if it's master or slave.
[/QUOTE]

Actually the sda disk is the master one. I'm not exactly sure where (during the Dapper installation) I get to determine where GRUB is actually installed. I don't remember anything specific in the process where I determine where Dapper installs it.

---

