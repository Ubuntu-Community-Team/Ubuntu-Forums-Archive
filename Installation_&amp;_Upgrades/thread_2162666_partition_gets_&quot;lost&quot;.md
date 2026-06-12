---
title: "partition gets &quot;lost&quot;"
date: 2013-07-15
forum: Installation &amp; Upgrades
---

### Post by dwlamb on 2013-07-15
I am attempting to install Kubuntu 12.10 on a Dell Precision 490. Last week I installed Kubuntu when I had only one drive installed.  It worked fine.  I physically migrated a second drive to the machine and now the first drive gets lost and I can't boot.

SATA-0 is a WD 160Gb
SATA-1 is a Toshiba 2Tb

After migrating the second drive, I decided to re-install the o/s for there were some changes I wanted to make.  During the install at the point it comes to set-up partitions the 160Gb at SATA-0 disk was not listed.  I ended the install and booted into PartedMagic to examine what might be wrong.  PartedMagic's partitioning tool, which I believe is GParted, saw the drive ok so I wiped it to nothing and carried out the Kubuntu installation.  This time it saw the drive and I completed the installation.  Upon reboot, I was presented with a text log-in instead of a gui.

I opted to install again and was met with what happened above; the drive was not listed at the partitioning stage of Kubuntu's installation.  I used GParted again and it sees the drive.  Another attempt at running the installation and upon reboot I was presented with a gui, but after installing some proprietary drivers that required a reboot, I was met with a text prompt again.  I rebooted and entered the BIOS set-up.

In the Drives section > SATA operation, the option was set to RAID Autodetect/ATA instead of RAID Autodetect/AHCI (the factory default).  Some research on the internet tells me that ACHI drivers should be part of install packages for Linux distros. I reset the option to RAID Autodetect/AHCI and took note of the warning I might not be able to boot into an existing o/s installation.

I reinstalled Kubuntu and the drive was visible.  Upon reboot, I was met with a gui, logged in and installed proprietary drivers for the video card.  Rebooting after that, I am prompted

error: no such partition.
grub rescue>

I am thinking this must be a driver issue.  Any time I boot into GParted, I am not met with the drive not listed. Not in the file manager, GParted or Clonezilla.  The diagnostics built-in on the Dell boot menu give a pass to both hard drives.  I have also

Any help would be greatly appreciated.

---

