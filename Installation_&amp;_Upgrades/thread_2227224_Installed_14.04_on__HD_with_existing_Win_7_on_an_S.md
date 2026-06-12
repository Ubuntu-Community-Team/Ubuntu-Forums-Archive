---
title: "Installed 14.04 on  HD with existing Win 7 on an SSD. Get boot menu OK but all Ubuntu"
date: 2014-05-31
forum: Installation &amp; Upgrades
---

### Post by carl15 on 2014-05-31
Hi

I last used Linux with Red Hat 7 [which had a significantly better install procedure than has Ubuntu!] so I'm pretty rusty... :)

After many hassles I eventually got 14.04 to install by using the  'install alongside Windows' option onto an unformatted 160GB partition  on my WD 1TB - it's on partition 3 (partition 1 is a 350 MB Windows  system partition, partition 2 is an 80Gb Win 8 partition (not used  currently - I loathe Win 8). I allowed the install to put grub on the default  volume (Samsung 840 Pro 256 GB SSD). Ubuntu formatted the space into a 142GB Linux partition and an 8GB swap partition. I ran offline (I have only Vodafone mobile BB at this location, & I'm sure the K3770 dongle will require a Linux-specfic package to be installed before Linux will run it).

After the install I rebooted  and got the grub menu OK. However, if I select any of the Ubuntu options (other  than those that require any code editing) the screen goes black and  nothing happens (I once waited >10 minutes).

System:

Intel i7-3770K @4.2GHz
Asus P8Z77-V LX2, UEFI, AHCI on.
2x4 GB Corsair Vengeance Red DDR3-1600 (XMP)
Gigabyte HD7950 3GB
Win 7 Pro 64 on SSD partition 1; 2 other logical partitions (ArmA 2 & Arma 3) plus 24 GB partition for overprovisioning 
1TB WD Blue - multiple partitions.
Acer 24" 1920 x 1200 monitor

I would like to get this working, but have no idea how to approach this. Since ir simply fails to boot I have no error codes or messages that might help :(

Kind regards

Carl

EDIT: I just had a look inside the Linux partition using DiskInternal's Linux Reader. Virtually all of the directories are empty. I recall seeing a long list of "Removing..." at the end of the "install" procedure - at the time I assumed that these were temporary files. Apparently not. Ubuntu 14.04 installed then deleted most of the installed files. 

Bah. What a waste of time.

By the way, the download checked out fine, the MD5 & SHA codes matched, the DVD burn was verified by CDBurnerXP, & I ran the 'verify disk' on starting the Ubuntu from that DVD. It passed. 
This has to be the worst installer I have ever encountered. Garbage...

---

### Post by LastDino on 2014-05-31
That nothing happening part might be due to driver issues, do you've graphic card? Try pressing F6 and select Nomodest 

As far as W7 not being seen could be issue with UEFI. Try reading this to get more info on how to dual boot.


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by carl15 on 2014-05-31
Sorry, maybe I wasn't sufficiently clear.

Win 7 is seen - in fact I'm running it now. Grub2 installation is fine - it is the only part of the install process that I find remotely acceptable.

The problem is that the Ubuntu installer has clearly DELETED almost every file at the end of the installation process. Folders like var, bin, sbin, dev, lib, home are present but totally empty. Nothing is seen because there isn't any Linux system to run...

This installer appears to be rubbish.

---

### Post by LastDino on 2014-05-31
I dunno man, I used the same installer and there weren't any empty directories here, is it possible that it was something else?

---

### Post by carl15 on 2014-05-31
Hi

I have no idea. 

I guess the only question I can pose that makes any sense now is: How do I safely get rid of it? Obviously deleting the partition (I love MiniTool for Windows :) loses all the useless empty directories, etc. However I want to get rid of the redundant Grub bootloader without fubaring the Win 7 installation.

---

### Post by oldfred on 2014-05-31
How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

Your Gigabyte card is nVidia. And with nVidia you have to use nomodeset on first boot or until you install the nVidia driver from the repository.
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

The installer does uninstall a lot of unused apps. I see it uninstall RAID & LVM for me as well as a lot others.
I suspect your viewer may not work correctly with ext4 partitions.

---

### Post by carl15 on 2014-06-01
> **oldfred said:**
> How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)



Thank you. I have a repair disk, ofc. Also have Acronis, and made an image of the Win 7 primary partition as a precaution so I could use that also, IIRC. 

Why on earth do Linux distributions not include an uninstaller that removes Grub/Grub2 when the user wishes to remove a Linux install from a dual-boot system? There is a tool on Sourceforge - I forget the name - but it seems to be available only as part of two large disk iso's (each many hundreds of MB, not a particularly friendly option if one is on moble BB).

> **oldfred said:**
> 
Your Gigabyte card is nVidia. And with nVidia you have to use nomodeset on first boot or until you install the nVidia driver from the repository.
      

No it is not. The HD7950 is an AMD Radeon product. nVidia cards have a distinctly different nomenclature.

 > **oldfred said:**
> 

The installer does uninstall a lot of unused apps. I see it uninstall RAID & LVM for me as well as a lot others.
I suspect your viewer may not work correctly with ext4 partitions.

Total size of the 'installation' is 5.25 GB according to Partition Wizard. The reader does not reflect that so perhaps you are right. According to the reader, the Linux partition has the label

/target

Maybe that suggests that the installation was defective?

I have never had a broken Windows install (from Win 3.1 to Win 8). I installed Red Hat 7 on 3 consecutive PCs with no significant issues.

Given that, e.g., [https://bugs.launchpad.net](https://bugs.launchpad.net),has many reports of serious errors with Ubiquity installs, I am not in the least tempted to proceed with Ubuntu. Ubiquity is not fit for purpose.

BR

Carl

---

### Post by travis-falkenberg on 2014-06-01
A simple way to have a look at what is installed is to just fire up the usb or cd live system you used to install Ubuntu. It will mount the partitions of your HDD which you can then view with the file manager. At least the live system will have full support for the filesystem you installed Ubuntu on rather than the unknown ability of Diskinternals Linux reader to read the file system.

You should be aware that disks/partitions are mounted read/write so you can damage your Windows installation if you are not careful. The live system also contains the graphical partition manager GParted which can be handy and dangerous of course so use it at your own risk.

Let us know what you find!

---

### Post by oldfred on 2014-06-01
There is one bug in the installer that is vital to avoid. It may not show Windows on a reinstall and says it will install over your previous install. But it is like the installs that do not see Windows and erases the entire hard drive.
So only use something Else or manual install and choose or create your own partitions.

/target just sounds like an auto mount name.

A partition of 5.25GB may not be big enough for just about anything. I normally suggest / (root) at 10 to 25GB and at 10 you need a separate /home and continuous maintenance to prevent it from getting to full.

---

### Post by carl15 on 2014-06-02
Thanks, Travis - as mentioned also by oldfred, the DiskInternals reader is not reading the files correctly despite the authors' claim that it reads ext4. The live Linux showed many, many more. I know the risks, but good that you point them out :)

---

### Post by carl15 on 2014-06-02
> **oldfred said:**
> There is one bug in the installer that is vital to avoid. It may not show Windows on a reinstall and says it will install over your previous install. But it is like the installs that do not see Windows and erases the entire hard drive.
So only use something Else or manual install and choose or create your own partitions.

/target just sounds like an auto mount name.

A partition of 5.25GB may not be big enough for just about anything. I normally suggest / (root) at 10 to 25GB and at 10 you need a separate /home and continuous maintenance to prevent it from getting to full.

I saw that (and other horrors) in the bug list.

Um, no. I decribed the space allocation in my OP: ~150 GB for Linux. It created a 142GB Linux partition and an 8GB swap partition. 5.25GB is the estimated size of the installation (i.e., sum of all files) in that 142GB partition.

On another note: while I used MiniTool's partition Wizard from the Win 8 install on the HD [sd1] to "rebuild MBR" on the SSD [sd0] (Win 7 on C is the active & boot partition), not all people who may want to remove Grub from a Windoze system might have more than one M$ installations. 

MiniTool also offers a free iso download that can be run from a CD/DVD or USB drive. Would likely be useful for people who have totally buggered their MBR and can't boot into any OS. It's only a 48MB download. Very useful tool for any Windows system. 

The big advantage for relatively inexperienced users is that it's simply a matter of running the program, clicking on the icon for the boot drive & selecting "rebuild MBR" from the tools -> apply ->exit & reboot nto Windows. Sequential command-line entries from a Win repair disk may be more worrisome/error-prone.

PS I have no connection whatsoever to MiniTool, I've just been a very satisfied user of their free tool for years. The in-Windows version works so well I've never had to use the standalone...yet.

---

