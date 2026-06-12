---
title: "Ubuntu 16.04.3 can't boot up automatically after powering up."
date: 2017-10-31
forum: Installation &amp; Upgrades
---

### Post by sunbear-c22 on 2017-10-31
After a system crashed, I  recovered all pertinent  files,  reformatted my entire disk and reinstalled Ubuntu 16.04.3 on the same system. However, I am encountering a very unusual behaviour. 

My system is not able to boot automatically when  powered up. It seems to be trap in an endless period of booting. I have to interrupt the booting by manually powering down the computer. After restarting the computer,  an American Megatrends Inc screen with the message that I fail to post and I need to press F1 appears. After pressing F1, the  uefi setup screen appears next, Here comes the unusual part....For ubuntu to boot up, I discovered that I have to  go to the  boot override section in the boot menu in the Advance mode, and manually click on the  disk with the installed Ubuntu. Then, the usual boot up of grub2 occurs followed by the rest....  I did notice that my disk  was not reported  in the American Megatrends Inc screen but it appeared in the UEFI. My disk name is BPX, I had to click on disk ubuntu(BPX) to boot up. Even though ubuntu(BPX) was select to be the first disk to bootup, the system  could not boot up automatically. After using Ubuntu, I am able to shutdown Ubuntu in the normal manner. So in short, my system just  can't boot up automatically when powered up.

Ubuntu 16.04.3 was installed in the following manner. I used a Ubuntu iso DVD. Sha256sum checked out. No updates downloading or 3rd party software install were selected. I had a blank disk and asked Ubuntu to install itself (i.e. installer  decided on the partitioning of my disk). 

Question: How can  my system   boot up automatically upon powering up?

---

### Post by sunbear-c22 on 2017-11-01
I did the following actions to restore automatic boot of Ubuntu 16.04.3 when powered up. 

1. Unified the type of partition table used for disks.
During my re-installation activity, I had changed the types of partition table used to partition my disks. Previously, my disks used Master Boot Record (MBR). Presently, they are using GUID Partition Table (GPT). Reasons I used GPT for my disks are (quoting from [Arch ]("https://wiki.archlinux.org/index.php/partitioning")) :
> If you are partitioning a disk of 2 TiB or larger, you need to use GPT.
It is recommended to always use GPT for UEFI boot, as some UEFI implementations do not support booting to the MBR while in UEFI mode.


I used GParted (GUI) to set up my disk:
a. Removed all existing partitions.
b. On Device menu, click "Create Partition Table... "
c. On new window, select "gpt".
d. One unallocated disk space in main GUI, right click mouse and select "New".
e. Set 1st partition: New Size="256MB", File System="fat32", Name="EFI System Partition", Label="EFI System"  and click "Add"
f.  Right click on the newly created partition, select  "Manage Flags", select "esp" and "boot" and finally click "close".

More explanations on [Grub2]("https://wiki.archlinux.org/index.php/GRUB") and [UEFI System Partition]("https://wiki.archlinux.org/index.php/EFI_System_Partition"). They applied to setting up a Ubuntu system too.
 

2.  Updated the bios of the motherboard. In my case, I downloaded the [latest Asus Z170M-plus bios]("https://www.asus.com/us/Motherboards/Z170M-PLUS/HelpDesk_Download/") and installed it. 


3. In Asus UEFI Advance Setting, for the safeboot EFI tab, I enable "Window" to ensure EFI boot.

---

### Post by Bashing-om on 2017-11-01
sunbear-c22 - :)

That you provided your solution.
Will be of great help to others seeking a similar solution .

Good work

---

