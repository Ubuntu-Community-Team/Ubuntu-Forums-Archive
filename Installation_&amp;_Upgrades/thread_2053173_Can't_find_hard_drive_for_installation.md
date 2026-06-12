---
title: "Can't find hard drive for installation?"
date: 2012-09-04
forum: Installation &amp; Upgrades
---

### Post by Jestry on 2012-09-04
Trouble finding a hard drive to install Ubuntu 12.04 on. 

As you can see, the 3.74 GB drive is the only one that is showing up. It seems that this is the USB that I am running Ubuntu from, and not an actual drive from the computer. Same thing happens when I try to install Ubuntu. The USB (with no free space) is the only drive that shows up. 

It seems that there should be an internal hard drive, but I don't know why it's not being recognized? This is a Gateway netbook that previously had Windows XP on it. If Win XP is causing the computer's harddrive to be hidden from gparted, how do I show it so I can free it up for Ubuntu?

EDIT: Tried removing [dmraid]("http://askubuntu.com/questions/56069/ubuntu-install-failing-hard-drive"), didn't help.

---

### Post by oldfred on 2012-09-04
Some computers promote a USB flash to sda. Does it show an sdb in upper right combo box?

I had a XP install's drive disappear in gparted even though XP still booted. I ran chkdsk on the NTFS partition and then gparted showed the sda or XP drive. (Windows then booted a tad faster also).

from terminal what does this show?

sudo fdisk -lu

sudo lshw -class disk

And if drive still not shown is it shown in BIOS? If not in BIOS then nothing will show it. Often loose connection, but could be bad drive.

---

### Post by Jestry on 2012-09-04
Not sure I totally understand your question, but this is what happens when I go to the drive-selection step of the installation. (screenshot attached)

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 4011 MB, 4011491328 bytes
77 heads, 13 sectors/track, 7827 cylinders, total 7834944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        8064     7834943     3913440    b  W95 FAT32

ubuntu@ubuntu:~$ sudo lshw -class disk
PCI (sysfs)

I was obviously accessing the drive fine in order to work win XP, so I don't think it's a connection issue?

---

### Post by oldfred on 2012-09-04
fdisk also is only showing the flash drive.

Does BIOS show you having a hard drive?

---

### Post by Jestry on 2012-09-04
Bios shows the windows partition as IDE... something. And the windows portion loads fine. I am assuming this is my hard drive.

I tried chkdsk on the C drive in windows, didn't help.

---

### Post by oldfred on 2012-09-04
IDE is a setting for how to read/configure the drives. It should list the hard drive(s) by manufacturer.

See attached for my list from BIOS, but every BIOS is different.

---

### Post by Jestry on 2012-09-05
This is a picture of my BIOS menu. The second option (IDE O) is the one that boots up to the win XP partition, also the one I can't access while on Ubuntu.

---

### Post by oldfred on 2012-09-05
BIOS is showing it but Linux is not seeing it??

Do you have settings to change drive to AHCI, that may not work with XP but will tell us if drive is seen. When I changed to AHCI, I stopped booting XP as it needs drivers that really should be installed with the initial install. But my new SSD needed AHCI. If not AHCI do you have Large or LBA as a setting instead of IDE?

Soon times other settings in BIOS may confuse system.

These are comments by others with issues, see if any apply.

> BIOS in not updated to latest revision
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA 6 Gbit/s  from 6 Gbs to a SATA II - 3Gbs 
BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Old BIOS, new drive 137GB max boot size or very large / partition over 100GB
[https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)
[https://help.ubuntu.com/community/CreateBootPartitionAfterInstall](https://help.ubuntu.com/community/CreateBootPartitionAfterInstall)
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on)
Old gpt data on drive
Disable Quickboot in BIOS
turning off UDMA in the BIOS my problem has gone away.(old system & may make system slower)
In the Asus BIOS I selected Advanced Mode>Advanced>SATA Configuration.
Changed IDE Mode to AHCI Mode
Then,when the SATA3G_1 selection appears in the drive list below,select the Enabled option.
set pci=nomsi or other boot paramter
So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!


---

