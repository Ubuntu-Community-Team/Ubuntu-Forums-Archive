---
title: "Grub error &quot;attempt to read or write outside of disk hd0&quot;"
date: 2020-06-04
forum: Installation &amp; Upgrades
---

### Post by Morgonte on 2020-06-04
I try to run a dual boot: Ubuntu Studio 19.4 and Win 7. The computer has 4 hd:s, Ubuntu Studio on sda2 and Windows on sdd1. Sda1 used to hold some data for the windows system but I erased it to make sda a linux/ext4 only drive. 

However, when I try to boot Ubuntu Studio from GRUB I get the error "attempt to read or write outside of disk hd0". I've tried Boot-Repair, but so far with the only result is that my windows boot has been messed up. The grub error persists. However, if I boot sda2 from UEFI:s boot menu It works just fine. 

Here's the data from Boot-Repair:

[http://http://paste.ubuntu.com/p/RF84WTpcRn/]("http://http://paste.ubuntu.com/p/RF84WTpcRn/")

How can I get Grub to work properly?

---

### Post by oldfred on 2020-06-05
Working link, is this yours?
[https://paste.ubuntu.com/p/RF84WTpcRn/](https://paste.ubuntu.com/p/RF84WTpcRn/)

With multiple drives & installs, only use Boot-Repair's advanced mode. You typically do not want one grub installed to all drives which is its default fix. In advanced mode you select install & drive to install boot loader into.

Install Windows boot loader to MBR of sdd. Boot-Repair may work and installs a Windows type boot loader, syslinux. But often better to use your Windows repair/recovery flash drive to run fixMBR command. Fixes will not work unless sdd1 has boot flag, so make sure you have a boot flag on that partition. You can use gparted or your Windows repair flash drive and set active.

Grub only boots working Windows. 
So if newer Windows 8 or 10, it may turn fast start up back on and then you have to directly boot by choosing it in BIOS. Also if it gets corrupted & needs chkdsk grub will not boot Windows. So always keep Windows boot loader in MBR of Windows drive.

It also looks like you have a 2.7 TB drive, but partitioned with MBR(msdos). MBR has a hard limit of 2TB, so you converted your 2.7 drive to 2TB. MBR was designed back in the 1980's when GB was very large and TB unheard of.

GPT info
[https://support.microsoft.com/en-us/help/302873/frequently-asked-questions-about-the-guid-partitioning-table-disk-arch](https://support.microsoft.com/en-us/help/302873/frequently-asked-questions-about-the-guid-partitioning-table-disk-arch)
[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://www.rodsbooks.com/gdisk/whatsgpt.html](http://www.rodsbooks.com/gdisk/whatsgpt.html)

Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

### Post by Morgonte on 2020-06-09
Thanks oldfred, for providing good suggestions. However, Whatever I tried, I couldn't get rid of the "outside of hd0"-error, neither can I get Win7 to boot... Finally I decided to get rid of ubuntu studio and install the latest linux mint. Mint seemes to work, but I do not get back windows, yet. 

but since I no longer have any *buntu flavour on my system, I guess my question is Off Topic now. I will have to seek advice somewhere else. Still, thaks a lot!

---

