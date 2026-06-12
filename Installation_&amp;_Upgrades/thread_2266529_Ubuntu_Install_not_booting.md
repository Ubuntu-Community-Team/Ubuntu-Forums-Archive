---
title: "Ubuntu Install not booting"
date: 2015-02-23
forum: Installation &amp; Upgrades
---

### Post by Robyn_Stegman on 2015-02-23
[FONT=arial]I've been running a Ubuntu install for a while but need Windows for work so I decided to try doing a dual boot. I downloaded Windows, deleted the original Ubuntu than reinstalled Ubuntu. GRUB 2 wasn't loading even after boot repair. It would just automatically boot in Windows.

[/FONT]
[FONT=arial]After troubleshooting for hours I finally gave up and decided to go back to only Ubuntu choosing to erase my previous operating system on the install. GRUB 2 is still not working and now it's not booting anything. I ran boot-repair again, this is what I got and it's still not working:[/FONT]
[http://paste.ubuntu.com/10376969/](http://paste.ubuntu.com/10376969/)


Any ideas of next steps?

---

### Post by oldfred on 2015-02-23
You seem to have a newer system that can boot either UEFI or BIOS.
So then you have to install both systems in the same boot mode to be able to dual boot. Or both must be UEFI or both must be BIOS and then UEFI set to only boot in that mode.

How you boot install media UEFI or BIOS is how it installs.

But if drive is already partitioned additional rules apply.
Windows only boots from a gpt partitioned drive with UEFI.
Windows and Ubuntu only boot from a MBR(msdos) partitioned drive with BIOS.

You have a gpt partitioned drive. 
To get Ubuntu install grub & boot in BIOS/MBR mode you need a 1 or 2MB unformatted partition with the bios_grub flag. But you cannot install and use Windows on gpt drive in BIOS mode.
Or if  you want to boot in UEFI mode, you must have a FAT32 formatted partition with the boot flag. Both Windows & Ubuntu use this same efi partition for boot files.

So I would suggest adding boot flag to sda1 with gparted from live installer booted in UEFI mode and use Boot-Repair to run the full uninstall/reinstall of grub. I do not think an auto fix does enough.
Then make sure UEFI is set for UEFI boot. 

Some systems may not easily boot 'ubuntu' entry in UEFI as vendors modify UEFI to only boot Windows. What vendor & model is this?

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

