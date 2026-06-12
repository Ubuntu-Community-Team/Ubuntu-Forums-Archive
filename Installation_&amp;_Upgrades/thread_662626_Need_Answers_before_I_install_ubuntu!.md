---
title: "Need Answers before I install ubuntu!"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by milentie on 2008-01-09
Hello!

There are some issues I have to resolve before i install Linux, and i need your help.

I have 2 hard disks on my pc each with 2 NTFS partitions (15gb and 65gb). One of them is SATA and it is my primary boot hd, and the other one is ata which is set to be primary slave by my dealer and i cannot open my pc due to waranty label to change it. I want to install Linux on my ATA primary slave hd on the 15gb ntfs partition. Can this be done?

My question is will there be problems in instalation and booting because i have WinXp running on my pc also installed on my sata primary drive and i dont want to delete it?

P.S. My dvdrw is set to be primary master!

Thanks!

---

### Post by Gina on 2008-01-09
I have successfully installed Ubuntu as dual-boot with Windows on 2 PCs without disturbing Windows in any way.  You use the Ubuntu partition editor to resize a partition to make free space for Ubuntu.  The latter requires 2 partitions (minimum) for the system and swap.  There are several sites showing haow to do this including the main Ubuntu site and here.  I have info on my [Ubuntu HowTo website]("http://www.ginad.org.uk") plus a list of links.

---

### Post by milentie on 2008-01-09
thanks gina, but another thing cencerns me, i just tried the live cd and the startup was ok, until the desktop apeared. it was all messed up, like halted windows dragging. and i couldn not see any icons or taskbar. will this be a problem after i install linux, or it was just from the live cd?

---

### Post by Kevbert on 2008-01-09
I have a single SATA drive on my AMD2 PC.  On this 160Gb drive I have the original XP Pro operating system as well as Ubuntu 7.10 standard and Ubuntu 7.10 64 bit.  I would suggest that it would be possible to install Ubuntu with care on the SATA drive providing that you have enough room on this drive (at least 10Gb) and that you have the Guided option when you Partition the disk (as part of the Ubuntu installation).
You can start the install program and it will ask you about timezone, keyboard etc.
Next the window 'Prepare disk space' will be displayed.  If you have the option 'GUIDED' and can set the partition size you can install Ubuntu, BUT if you only have 'GUIDED - use entire disk' and it isn't your 15Gb drive cancel the install.  If you proceed after this point all data on the selected drive or partition will be lost.
The most important thing is to backup everything prior to installing a new operating System.

---

### Post by Borbus on 2008-01-09
The desktop will run much quicker once you have your proper graphics drivers installed. The LiveCD can't use the proper graphics drivers. When you install Ubuntu on to your hard disk you can easily install Nvidia or ATI drivers using the Restricted Drivers Manager.

---

### Post by Gina on 2008-01-09
> **milentie said:**
> thanks gina, but another thing cencerns me, i just tried the live cd and the startup was ok, until the desktop apeared. it was all messed up, like halted windows dragging. and i couldn not see any icons or taskbar. will this be a problem after i install linux, or it was just from the live cd?
Try the second boot option for safe graphics mode.

---

