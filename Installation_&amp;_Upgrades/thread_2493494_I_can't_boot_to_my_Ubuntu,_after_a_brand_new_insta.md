---
title: "I can't boot to my Ubuntu, after a brand new install of Windows on a new SSD"
date: 2023-12-17
forum: Installation &amp; Upgrades
---

### Post by ew0ny on 2023-12-17
I had issues with my SSD that was running Windows (really poor health), I got a new one and installed a brand new install of Windows 11. Then when I rebooted afterwards I was seeing black screen with ```
failed to open \EFI\UBUNTU\grubx64.efi - not found
```.

The first thing I did was to setup a Ubuntu bootable USB, and use Try-Ubuntu feature to access the terminal and install and fix my issues with boot-repair, the issues was that I could only get info about the issue, there wasn't a recommended fix button at all. I started to panic after that :D.

Here is the [pastebin ]("https://paste.ubuntu.com/p/bxybJmNkYN/")I got from boot-repair, I'm really not sure what can I do.

---

### Post by Rubi1200 on 2023-12-17
I hope you had a good backup of your Ubuntu install. I don't see any version of it installed, only remnants of the boot files presumably from the previous installation.

Wait for others to comment, but be prepared to do a fresh install.

Sorry the news is not more positive.

---

### Post by tea for one on 2023-12-17
Two versions of Windows but no sign of Ubuntu
Line 102 - OS#1:   Windows 8 or 10 on nvme0n1p2
Line 103 - OS#2:   Windows 10 or 11 on nvme1n1p2

Both systems seem to be installed in Legacy/mbr mode as shown by:-
Line 5 - Windows is installed in the MBR of /dev/nvme0n1.
Line 6 - Windows is installed in the MBR of /dev/nvme1n1.

If you look at lines 217 - 231, there aren't any Linux partitions.

Your disk sda has an ESP containing an Ubuntu boot file but the disk only has ntfs and vfat partitions.
Was Ubuntu originally on this disk?
> 
I'm really not sure what can I do. 
Briefly.
Back up your data
Re-install Windows 11 on one disk in UEFI mode with GPT
Install Ubuntu 22.04 on second disk in UEFI mode with GPT
Only have the target disk available when installing so that each disk has an ESP.

---

### Post by yancek on 2023-12-17
I expect you have not had much experience installing operating systems based on the information you posted.  As others have indicated, you overwrote your Ubuntu install completely by not selecting the proper drive..  I've not installed windows 11 but, with windows 10 there was a Custom install option which allows the user to select specific drives/partitions or free space on which to install.  This was immediately after the EULA page at the beginning of the install.  Might bear this in mind for future installs.  Another simple thing to do is to disconnect all physical drives you do not want to install to if possible.

Does your windows boot?  I would expect not as you don't have any EFI partition on the SSD drives, both of which are GPT.  Is the drive referred to as sda the old drive still attached which has the EFI partition and boot files?

---

### Post by ew0ny on 2023-12-17
Thanks for all of the comments. 

I'm familiar with Partition stage of the Windows installation, and really didn't format the SSD that contained my Ubuntu. I selected my new SSD, formatted it, and continued with the installation. I can access both of my Windows 11 installation, running on those two separate SSD's but not the Ubuntu. 

I was afraid of that scenario, but seems I made a huge mistake not firstly unplugging my drives.

---

### Post by ew0ny on 2023-12-17
I believe this has something to do with my SSD containing the Ubuntu, because I can't seem to find it connected via BIOS, I can see that 2 x M2 slots are taken, and 1 SATA, but actually should be 2 SATA (one for my SSD and one for my HDD)

---

### Post by tea for one on 2023-12-17
Remove the three known disks and see if the "unknown" disk boots into Ubuntu.

---

