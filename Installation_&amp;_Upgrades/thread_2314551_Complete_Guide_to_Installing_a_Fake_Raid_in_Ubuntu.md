---
title: "Complete Guide to Installing a Fake Raid in Ubuntu"
date: 2016-02-22
forum: Installation &amp; Upgrades
---

### Post by nicolas59 on 2016-02-22
[SIZE=5]Hello, and thanks for reading.[/SIZE][B]

[SIZE=7]A Complete Guide to Installing a Fake Raid in Ubuntu[/SIZE][SIZE=3].

[/SIZE][/B]This guide will educate and explain all aspects regarding installing a fake raid in Ubuntu, if for some reason you are unable to install a software raid.


Some of the problems you can encounter when installing a fake raid are:

[LIST]
[*]Raid array not being detected by the installer
[*]Stuck on 'Creating EXT4...'
[*]Error installing grub (Courtesy of *will reference later*)
[/LIST]
This guide will also provide information regarding what bios settings to run in, what partition tables to use etc.

[SIZE=7]1. BIOS SETTINGS
[SIZE=2]
It is not immediately clear what settings to use, simply put the setting one needs first are:** [SIZE=3]RAID AND LEGACY[/SIZE]**

This enables the user to edit raid arrays while supporting windows and linux communication via hard disk (if necessary). An example would be if I needed windows to run a specific program I have on linux.

[SIZE=7]2: Partitioning Windows. IF UNNEEDED Skip to 4
[/SIZE]
Installing Windows is usually a good idea in case Wine doesn't cut it. 

[B]Assuming you have a windows and linux bootable flash drive, insert the linux one now.

Boot into linux live[/B] off the flash drive, do not choose to install or go into the raid array options just yet.
[B]
Open Gparted. [/B](your best friend)

[B]Pick the disk you are sacrificing for windows and create a new MDOS partition.

Reboot, and insert the WINDOWS flash drive[/B]

[SIZE=7]3. INSTALLING WINDOWS [/SIZE]

**Boot into windows and make sure to select the settings which installs it on the correct drive.** Windows is foolproof, it should be easy.

[B][SIZE=4]After that windows should be installed correctly, ready for the linux dual boot.
[/SIZE][/B]
[SIZE=4][SIZE=7]4. Partitions, Linux and You. [/SIZE][/SIZE]

**Windows flash drive is unneeded now**. You may burn it.

**Boot into linux live.**

**Open Gparted and create a GPT partition table on all RAID disks. DO NOT CLICK THE WRONG ONE OR ALL DATA SPECIFICALLY THE WINDOWS PARTITION WILL BE LOST**

**Reboot and configure the raid array. My hotkey was CTRL + I**
[/SIZE][SIZE=2]
[B]Reboot after configuring the raid array and boot into linux live again.
[/B]
[/SIZE]5. INSTALLING UBUNTU
[SIZE=2]
[B]Open Gparted, and create a new GPT partition table on the new raid array. DO NOT CREATE AN EXT4 PARTITION. THIS WILL SOLVE IT BEING STUCK IN THE INSTALLER.

[/B]Congrats, everything is now configured correctly for installation.

[B]Open Install Ubuntu.

[/B]**Go through the installer**. I don't see a reason to use manual partitioning, but make sure to select the correct drive when doing so.

[B]Click 'Install ubuntu alongside Windows'.

If done correctly, there should be no problems until GRUB complains. If it doesnt, consider yourself lucky and enjoy. If not, keep reading.

[/B][SIZE=7]6. GRUB AND YOU[/SIZE][B]

ATTEMPT TO INSTALL GRUB ON ANOTHER DISK IF IT ASKS YOU TO. THIS MAY FIX YOUR PROBLEM

If like me it doesnt install correctly, boot into linux live one last time.

Run these commands: 

[/B][/SIZE][/SIZE][FONT=monospace]sudo [/FONT][FONT=monospace]apt-add[/FONT][FONT=monospace]-repository ppa:yannubuntu/boot-repair[/FONT]
[FONT=monospace]sudo apt-get update[/FONT]
[FONT=monospace]sudo apt-get install -y boot-repair[/FONT]
[FONT=monospace]boot-repair
[/FONT][SIZE=7][SIZE=2][FONT=arial]This will install a BEAUTIFUL program which will repair GRUB

[/FONT][B]Click recommended repair and go through all the steps. When installing grub again, pick ALL the hard drives. Reboot when finished.

[SIZE=3]CONGRATULATIONS, YOU HAVE FINISHED THE GUIDE. I hope this helps, as the reason I wrote this was because there was a lack of instructions regarding this topic. 

Thanks for reading.[/SIZE][/B]
[/SIZE]
[/SIZE]

---

