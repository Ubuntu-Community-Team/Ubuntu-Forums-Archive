---
title: "Multi OS on RAID 0 array"
date: 2011-11-24
forum: Installation &amp; Upgrades
---

### Post by megahertz on 2011-11-24
**How to install Ubuntu and Windows operating system on a RAID 0 array.**:D
(November 2011)

I have spent a week to setup Ubuntu 11.10 on a Raid 0 array configuration with multi operating systems (windows 7 64, Windows XP 64 and Ubuntu 64). I want to share my experience and what I learned.
It's something insane even for an Linux expert, and I'm not a Linux expert. I have search the forums and found many people with the same problem, but no one has fond a simple solution. I will try to explain what I did to finally have my Ubuntu installed on a Raid 0 array.

**Introduction**
In Linux, you have three different Options to build a Raid (Redundant Array of Independent Disks):
- Hardware Raid - Where the Array is built and is controlled by a independent and dedicated hardware. As the Array is built and is controlled by hardware at low level you can have multi operating systems installed.
- Fake Raid - Where the Array is built and is controlled by the motherboard chip set and setup on BIOS environment. As the Array is built and is controlled by hardware at low level you can have multi operating systems installed.
- Software Raid- Where the Array is built and is controlled by Linux software. As the Array is built and is controlled by Linux software you can NOT have multi operating systems installed.

There are many ways to configure a Raid, but the most used are: ([http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID))
**Raid 0** - (block-level striping) - A pair of disks where data is divided in blocks and stored alternatively in one disk and the other. It provides improved performance and additional storage but no fault tolerance. Hence simple stripe sets are normally referred to as RAID 0. Any drive failure destroys the array, and the likelihood of failure increases with more drives in the array (at a minimum, catastrophic data loss is almost twice as likely compared to single drives without RAID). A single drive failure destroys the entire array because when data is written to a RAID 0 volume, the data is broken into fragments called blocks. The number of blocks is dictated by the stripe size, which is a configuration parameter of the array. The blocks are written to their respective drives simultaneously on the same sector. This allows smaller sections of the entire chunk of data to be read off the drive in parallel, increasing bandwidth (size and speed). RAID 0 does not implement error checking, so any error is uncorrectable.

**Raid 1** - (mirroring without parity or striping) - A pair of disks where data is written on both disks. The array continues to operate as long as at least one drive is functioning. It's a redundant system, used for safety reasons.

**Raid 01** - (mirrored sets in a striped set) - Basically is two pairs of disks, each pair in Raid 0, and the two pairs in Raid 1. Four disks are required, but you have the speed and size of Raid 0 and redundancy of Raid 1.

Every new motherboard comes with the option to build a BIOS Raid (fake Raid) as a Raid 0, Raid 1 or Raid 01 configuration. Then setting up Ubuntu on a BIOS Raid (fake Raid) should be as simple and as easy as with a single HD. It should, but it's a nightmare.

The problem is that the Ubuntu desktop installation software comes with and loads the Raid manager software (dmraid), but it doesn't install it on target drive. The second main problem is that you're not able to install the boot loader (Grub), maybe because dmraid hasn't bean installed.

I will explain, detailed as possible, what and how I did to finally have windows7-64, Windows XP-64 and Ubuntu installed on a Raid 0 array.


**Steps**
There are many. I advise you to read and try to understand all the steps first, before proceeding with your installation.
I used three WD 500G SATA 3 HD's. Two for building the Raid 0 array (sda and sdb) and one (sdc) as an installation toll and for backup.

 1) – Windows XP installation on the sdc HD.
 2) – Building the Raid 0 with sda and sdb.
 3) – Partitioning and formating the Raid 0 array.
 4) – Windows XP and Windows 7 Installation on the Raid 0 array.
 5) – Windows 7, Windows XP and Ubuntu boot loader configuration on the Raid 0 array.
 6) – Making ubuntu-11.10-desktop and ubuntu-11.10-alternate bootable USB disk.
 7) – Finding Raid partitions path.
 8) – Installing Ubuntu.
 9) – Final adjustments.
 10) – Installing gnome GUI (optional)

**Step 1 - Win XP Installation on the sdc HD.**
- With a Raid 0 array you get twice the space and almost twice the speed of a single drive, but it's more than twice the risk of loosing everything than with a single drive. Just a hardware fail on one drive, or even a logic operation fail, and all data is lost.
That's why I have setup a backup single drive with Win 64 and a synchronizing software on it.
- On another computer with Windows 7 64 and nlite software I've created a customized Win XP 64 installation disk with SP2 and Intel Raid drives on it.
- On the target computer motherboard (GA Z68A D3-B3) BIOS setup, I configured it to enable the BIOS Raid software.
- I attached the  sdc HD to the SATA 2 socket and the CD&DVD drive to SATA 3 socket.
- I booted with the customized Win XP 64 installation disk and installed Win XP 64 on the sdc HD. When finished I installed the MB and Video card drives. After rebooting I installed Pwhe7, a very good shareware partitioning software.
- I shutdown the computer.

**Step 2 - Building the Raid 0 with sda and sdb.**
- I attached the  sda and sdb HDs to the SATA 0 and SATA1 sockets.
On the Motherboard (GA Z68A D3-B3) BIOS RAID setup, I configured the two HDs (sda and sdb) as a Raid 0 array.

**Step 3 - Partitioning and formating the Raid 0 array.**
- Booted Win XP on sdc HD and with Pwhe7 partitioning software I create and formatted the partitions as below:
	- 1# partition: 100M, NTFS, active, labeled as System, for boot loaders.
	- 2# partition: 60G, NTFS, labeled as Win 7, for  Windows 7 HP 64.
	- 3# partition: 40G, NTFS, labeled as Win XP, for Windows XP 64.
	- 4# partition: 8.2G, as Linux Swap.
	- 5# partition: 22G, Linux ext4, for Ubuntu.
	- 6# partition: 860G, FAT32, labeled as Data, for my files and folders.
- I shutdown the computer.
- I detached the  sdc HD from the SATA 2 socket.
[B]
Step 4 - Win XP and Win 7 Installation on the Raid 0 array.[/B]
- I booted with the customized Windows XP 64 installation disk and installed Win XP 64 on the third Raid partition. When finished I installed the MB and Video card drives. Windows XP boot loader files were installed on first Raid partition (active partition).
- I Shutdown the computer.
- I booted with Windows 7 HP 64 installation disk and installed Windows 7 64 on the second Raid partition. When finished I installed the MB and Video card drives. Windows XP boot loader files on first Raid partition (active partition) were replaced with Windows 7 boot loader files. Dual boot option (Win 7 as default and Win XP) under Windows 7 boot loader were created.

**Step 5 - Windows 7, Windows XP and Ubuntu boot loader on the Raid 0 array.**
- Under Windows 7, I've installed EasyBCD2.1, a good shareware software. With EasyBCD I edited Windows 7 boot loader configuration BCD file. With it, I renamed the Windows XP entry and added an Ubuntu option. To add an Ubuntu option, select the add tab. On the right, select Linux/BSD and on Type option, choose Grub 2 and on Name option write Ubuntu and hit the Add Entry button. EasyBCD creates a new entry option (Ubuntu) to your win 7 boot loader menu. The Ubuntu option is linked to a \NST\AutoNeoGrub0.mbr file of the active partition (System). During boot, a menu will show up with a Ubuntu option. When you choose Ubuntu, it will look for a Grub 2 on the drive and boot with it. If it doesn't find on the drive it will look for on other drives. Very good!!!

**Step 6 – Creating ubuntu-11.10-desktop and ubuntu-11.10-alternate bootable USB disk.**
- To install Ubuntu on the Raid array you will need ubuntu-11.10-desktop-amd64 and ubuntu-11.10-alternate-amd64 bootable CD's or USB flash drives (pendrive). I did with two USB flash drives (pendrives). 
- You will need two USB flash drives (pendrive) with at least 1G, one for ubuntu-11.10-desktop-amd64 and other for ubuntu-11.10-alternate-amd64.
- Under Windows 7-64, download ubuntu-11.10-desktop-amd64.iso, ubuntu-11.10-alternate-amd64 and Universal-USB-Installer-1.8.6.8.exe.
- Launch Universal-USB-Installer, choose the location of the targeton pendrive and select ubuntu-11.10-desktop-amd64.iso as source. Make the  ubuntu-11.10-desktop-amd64 bootable pendrive.
- Shutdown and boot with the Ubuntu-11.10-desktop-amd64 bootable pendrive.
- Choose “Try Ubuntu without installing”. You will end with Ubuntu running.
- Insert the second USB flash drive (pendrive).
- On the icons menu bar, hit the first icon and find and launch “Start up disk creator”. 
- Choose the location of the target pendrive and select ubuntu-11.10-alternate-amd64.iso as source. Make the ubuntu-11.10-alternate-amd64 bootable pendrive. It's very important to built the alternate pendrive under Ubuntu. If you do it with the Universal-USB-Installer it won't boot properly.

**Step 7 – Finding Raid partitions path.**
- The controllers supported by dmraid are (sudo dmraid -l):
asr     : Adaptec HostRAID ASR (0,1,10)
ddf1    : SNIA DDF1 (0,1,4,5,linear)
hpt37x  : Highpoint HPT37X (S,0,1,10,01)
hpt45x  : Highpoint HPT45X (S,0,1,10)
isw     : Intel Software RAID (0,1,5,01)
jmicron : JMicron ATARAID (S,0,1)
lsi     : LSI Logic MegaRAID (0,1,10)
nvidia  : NVidia RAID (S,0,1,10,5)
pdc     : Promise FastTrack (S,0,1,10)
sil     : Silicon Image(tm) Medley(tm) (0,1,10)
via     : VIA Software RAID (S,0,1,10)
dos     : DOS partitions on SW RAIDs

That means that if you have a Intel Raid controller, your raid partition will have a path of /dev/mapper/isw_yzyzyzyzyz_Raidn, if it's a Adaptec HostRAID,  your raid partition will have a path of /dev/mapper/asr_yzyzyzyzyz_Raidn etc, etc.
- Lauch terminal and type sudo fdisk -l
- Find and write down the Raid partition path where you want to install Ubuntu.
Now attention on the names (in my case)
	-Partition 1 (System)= /dev/mapper/XXX_yzyzyzyzyz_Raid1
	-Partition 2 (Win7-64)= /dev/mapper/XXX_yzyzyzyzyz_Raid5
	-Partition 3 (WinXP-64)= /dev/mapper/XXX_yzyzyzyzyz_Raid6
	-Partition 4 (Linux Swap)= /dev/mapper/XXX_yzyzyzyzyz_Raid7
	-Partition 5 (Ubuntu)= /dev/mapper/XXX_yzyzyzyzyz_Raid8
	-Partition 6 (Data)= /dev/mapper/XXX_yzyzyzyzyz_Raid9
I installed on Partition 4 (Linux Swap) and Partition 5 (Ubuntu) that has a Raid path /dev/mapper/isw_bicifbbaac_Raid7 (Linux Swap) and /dev/mapper/isw_bicifbbaac_Raid8 (Ubuntu).

**Step 8 – Installing Ubuntu.**
- Shutdown and boot with the Ubuntu-11.10-alternate-amd64 bootable pendrive created on step 6.
- Choose “Install Ubuntu”. When it ask if you want to Activate Serial ATA RAID devices answer Yes.
- On Partition Disks, be sure to select the Serial ATA RAID where you want to install. It should be something like /dev/mapper/XXX_yzyzyzyzyz_Raid8. Be careful. Don't select entire disk or other partition.
- When asked where to install Grub boot loader, write the same path where you installed Ubuntu (/dev/mapper/XXX_yzyzyzyzyz_Raid8). Don't install anywhere else.
- Shutdown, remove the Ubuntu-11.10-alternate-amd64 bootable pendrive and boot.
- On the Windows 7 boot loader menu choose Ubuntu. If you did everything right, you will boot Ubuntu with Unity GUI.

**Step 9 – Final adjustments.**
- Open Terminal and type sudo nautilus
- Hit Enter
- Nautilus file manager is launched as root.
- Make folder /etc/grub.d/original
- Move file /etc/grub.d/30_os-prober to folder /etc/grub.d/original
- Go to /etc/initramfs-tools and open (edit) modules file and add at the end
	raid0
	dmraid
	md-raid0
- Save
- Go to /etc/default and open (edit) grub file and change GRUB_TIMEOUT=10 to GRUB_TIMEOUT=2. Save
- Close nautilus.
- On Terminal type sudo update-initramfs -u
- Hit Enter.
- On Terminal type sudo update-grub
- Restart the computer.
- Launch the update manager to update Ubuntu.

**Step 10 – Installing gnome GUI (optional)**
- Open Ubuntu Software Center and search for “gnome shell”.
- Install it.
- Log off.
- On the log in screen hit the sun on the up right corner. Choose Gnome Classic.
- Log in.
- Place mouse over the Panel, press Alt+right mouse button. Choose Add to panel.. and customize to your preferences.

I have two questions to the Ubuntu developers::(
- How can you deliver (again) an installation software with a big bug like this?
- Why don’t you merge the two versions (desktop and alternate) to a DVD iso file. It’s not the first time that I have to download and burn the two versions.

Megahertz

---

### Post by ptrakk on 2011-11-24
gnarly! i saved this thread.

---

### Post by darkod on 2011-11-24
This will probably help some people, but to cut the story short:
As long as you use the alternate cd to install RAID (fake or soft), you should be fine. Most problems I've seen appear because people keep ignoring the recommendation and use the desktop cd which can see the fakeraid but in most cases doesn't install grub2 correctly.

---

### Post by hansel49 on 2013-01-28
oh my goodness" what for mess" and there is no response from the developers 
i want to install raid on ga 970a d3

---

### Post by lisati on 2013-01-28
If a thread hasn't had a reply for over a year, it's usually best to start a new thread. A lot can happen in the space of a year.


Old thread closed.

---

