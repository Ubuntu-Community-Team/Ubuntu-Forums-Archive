---
title: "[Ubuntu]Issue with dual boot with windows"
date: 2015-11-17
forum: Installation &amp; Upgrades
---

### Post by federico20 on 2015-11-17
[COLOR=#111111][FONT=Ubuntu]I've been struggling with ubuntu installation in the last few days. I got a new Lenovo B50-80 with FreeDos and wanted to install Windows 7 or 10 alongside with Ubuntu 14.04 on a Samsung SSD 840 drive.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Here is what I did:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]1)Installed Windows 10 by usb then tried to install ubuntu from usb but it didn't recognize windows even though it could see the different partitions. I left some unpartitioned space but when I created the partition it said that it didn't find the Boot partition or something.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]2)Tried installing Windows 7 from cd rom and then again ubuntu (usb stick) in both UEFI and Legacy mode but this time it couldn't even see the different partitions and was just showing everything unallocated.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I'm kinda desperate at the moment, any advice?I will post more details if tell me what you need (and maybe how to do it, I'm quite newbie with linux)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]thanks[/FONT][/COLOR]

---

### Post by oldfred on 2015-11-17
What brand/model system? And what video card/chip?

I think Windows 10 will default to UEFI mode with gpt partitioning if hardware is newer & UEFI.
But Windows 7 defaults to BIOS on MBR and from DVD usually not set to install in UEFI mode. It has to be copied to flash drive and slightly reconfigured with UEFI/EFI boot files.

Post this from terminal in live installer:
sudo parted -l

If UEFI you may want to review info in link in my signature. It is a lot but often necessary.

---

### Post by federico20 on 2015-11-17
I'm using a Lenovo B50-80 with i5 5200U with integrated HD5500 (I believe).
How can I use the terminal from the live installer?

---

### Post by Vladlenin5000 on 2015-11-17
Lenovo B50-80 is a business class laptop with quite standard hardware, including the integrated Intel graphics. No major issues should be expected with Ubuntu in that machine.

In a live session you use the terminal in the exact same way as in an installed system: Search in the dash or use the keyboard shortcut CTRL+ALT+T.

---

### Post by grahammechanical on 2015-11-17
A wild guess based in ignorance.

If Ubuntu is installed in UEFI mode then it will expect/need a EFI boot partition. It will use any Windows 8/10 EFI boot partition if one exists. Is that what is missing when this message was given?

> [COLOR=#111111][FONT=Ubuntu]it said that it didn't find the Boot partition or something.[/FONT][/COLOR]

Were you using the Install Alongside option or the Something Else option? So, Ubuntu being installed in UEFI mode + using the Something Else option would require that both the Ubuntu partition ( / ) and the EFI boot partition be indicated. Yes? No? As well as a swap partition.

Regards.

---

### Post by oldfred on 2015-11-17
I usually search for it in dash just like any app. Then pin it to the left to make it easy to get to. But I do not use Unity much as I install gnome-panel or fallback which is the old gnome2 look alike to menu system that old versions of Ubuntu used. Cannot teach old dog new tricks. :)

       [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by federico20 on 2015-11-17
> **oldfred said:**
> What brand/model system? And what video card/chip?

I think Windows 10 will default to UEFI mode with gpt partitioning if hardware is newer & UEFI.
But Windows 7 defaults to BIOS on MBR and from DVD usually not set to install in UEFI mode. It has to be copied to flash drive and slightly reconfigured with UEFI/EFI boot files.

Post this from terminal in live installer:
sudo parted -l

If UEFI you may want to review info in link in my signature. It is a lot but often necessary.

Here is what I get:

```
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No?
```

I then press Ctrl+C and get:

```
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags


Model: USB2.0 FlashDisk (scsi)
Disk /dev/sdb: 4007MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  4007MB  4007MB  primary  fat32        boot


```


> **Vladlenin5000 said:**
> Lenovo B50-80 is a business class laptop with quite standard hardware, including the integrated Intel graphics. No major issues should be expected with Ubuntu in that machine.

In a live session you use the terminal in the exact same way as in an installed system: Search in the dash or use the keyboard shortcut CTRL+ALT+T.

Oh, I feel so stupid right now. Basically the word "Live" was tricking me. I know how to use the terminal but I actually realized what Live was meaning, all is making sense now. (I'm not english)

> **grahammechanical said:**
> A wild guess based in ignorance.

If Ubuntu is installed in UEFI mode then it will expect/need a EFI boot partition. It will use any Windows 8/10 EFI boot partition if one exists. Is that what is missing when this message was given?



Were you using the Install Alongside option or the Something Else option? So, Ubuntu being installed in UEFI mode + using the Something Else option would require that both the Ubuntu partition ( / ) and the EFI boot partition be indicated. Yes? No? As well as a swap partition.

Regards.

I realized I wasn't quite clear, let me explain better. What it actually happens is that no operating system is detected by Ubuntu installer so the option "Install alongside windows" doesn't even show up. I get "Wipe all, clean installation" and Something Else option. I should just get the first option and run the installation smoothly like I did many other times before (on other computers) but it just won't go. I tried installing in both mode changing bios settings (and I actually got two different screen the black one and the purple one) but neither worked.

---

### Post by oldfred on 2015-11-17
If you installed a newer copy of Windows it boot so slow that it has to use hibernation all the time. They call it fast start up, but really just hibernation. 
But Linux NTFS driver will not mount a Windows partition that is hibernated or needs chkdsk. And NTFS always needs chkdsk after a resize. 
So make sure chkdsk has run at least once with no errors and make sure fast start up is off.

       Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
More explanation of NTFS driver & Windows hibernation
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

---

### Post by federico20 on 2015-11-18
> **oldfred said:**
> If you installed a newer copy of Windows it boot so slow that it has to use hibernation all the time. They call it fast start up, but really just hibernation. 
But Linux NTFS driver will not mount a Windows partition that is hibernated or needs chkdsk. And NTFS always needs chkdsk after a resize. 
So make sure chkdsk has run at least once with no errors and make sure fast start up is off.

       Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
More explanation of NTFS driver & Windows hibernation
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

I'm running windows 7 at the moment. Also I installed Samsung magician and switched off Hibernation (to extend SSD lifetime) with it.

I checked the disk from windows and tried again to install ubuntu, but nothing has changed. 
I really don't know what to do at this point.

EDIT: A little update, I found this post
```
[COLOR=#111111][FONT=Ubuntu]I had the exact same problem with dual booting Ubuntu and Windows on an HDD. Here is the solution to MBR and GPT problem: 
Boot from USB Stack or CD/DVD and select Try Ubuntu.[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]In the terminal while “booted” from the live CD type “sudo gdisk /dev/sda”
 (change “/dev/sda” to whatever is appropriate to access your hard disk, if necessary). 
The program is likely to complain that it’s found both MBR and GPT data, and will ask which to use. It doesn’t matter which you tell it to use.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]At the “Command” prompt, type “x” to enter the experts’ menu.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]At the “Expert command” prompt, type “z” to “zap” (destroy) the GPT data.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Type “y” in response to the confirmation about destroying the GPT.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Type “n” in response to the query about blanking the MBR. Caution: If you answer “y” here, you’ll destroy your Windows partition(s)![/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]There! Problem solved![/FONT][/COLOR]
```
I tried that and now the Ubuntu installer still can't detect windows BUT if I choose "Other" option I can at least see the partitions:

```
/dev/sda1   ntfs  104     MB
/dev/sda2   ntfs  121634  MB
/dev/sda3   ext3  123487  MB
free space        4830    MB
```

Where sda3 should be the partition I created from windows manually. And sda1 and sda2 should be the parts used by windows.

EDIT2: Seems like the last thing I did fixed the hole thing. I had to run the installation from usb in Legacy mode to "install alongisde windows 7" to pop out. 
thanks for your time. I hope the post will help someone else with the same problem.

Everything is working fine, except I have this graphic artifact (I don't know how to call it) just after selecting the Windows 7 option in the boot loader menu. 

> [IMG]http://s1.postimg.org/pumxks5a7/20151118_120023.jpg[/IMG]

this last for just a second or two and then windows start to boot normally

---

