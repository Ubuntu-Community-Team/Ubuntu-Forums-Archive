---
title: "I'm just a noob that wants to install linux HELP!!"
date: 2020-08-06
forum: Installation &amp; Upgrades
---

### Post by dev197 on 2020-08-06
I've been trying to install the new update for Lubuntu 20.04 for the last three days. Every time I install it gets to 10% and then I get this message: Bost.Python error in job "unpackfs"

Second time I tried using UEFI mode (and it was not in safe mode) and manual partition is my only choice (but I dont know how to manual partition). The menu option to check the drive doesn't show up any more, when the boot process starts I have a black page with similar options but i dont have the blue page (not sure if this is a problem or not). 

I downloaded both the iso and rufus multiple times but still nothing, I checked the md5sums and it matched (i was so proud for figuring that out lol) but still nothing.
Rufus settings:
Partition scheme: GPT       Target system: UEFI
File system: NTFS             Cluster size: 2K

I heard that unmounting worked for someone so i looked into that, and sda1 could be unmounted sda2 couldn't (using KDE Partition Manager and QTerminal).

When get to the partition section of the install my only option rn is manual partition; my current Partitions: sda1 300 MiB FAT32      sda2 931.2 GiB ext

P.s. Sorry for writing so much but I'm new to this so I don't know what information is going to be relevant and I dont want to miss anything. I'm %99 sure my main hardrive has been completly wiped so there is no going back now.

---

### Post by oldfred on 2020-08-06
Best to use Windows to shrink the NTFS partition to make unallocated space.  If that is NTFS.
If Windows hibernation is on, then Linux NTFS driver cannot correctly see the NTFS partitions. Turn fast start up off as that sets hibernation flag.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Default UEFI install is now just the ESP which you already have and / (root). But if larger space desired for Ubuntu better to have separate /home, but not required. Make sure drive is gpt partitioned.
If making entire drive just for Ubuntu use 300 to 500MB for ESP, 30 to 50GB for / (root) and rest for /home using Something else. 

Be sure to have good backups.

See my link below for basic install steps. And links for more details if you do not understand any step.

What brand/model system? What video card/chip as some may need boot parameters or settings.

If partitioning in advance with gparted:
Select gpt under device, advanced over msdos(MBR) default partitioning before starting.

---

### Post by dev197 on 2020-08-06
Im pretty sure the hard drive was wiped when i first tried the install so, i don't think i even have windows on my pc anymore. Can i turn fast startup off while using the linux that boots from my flash drive. Also are /home and /root supposed to be partitions I'm confused.

I have a Dell but I don't know anything else and I cant go into control panel how do i find [COLOR=#000000]model/video card without using windows?[/COLOR]

---

### Post by oldfred on 2020-08-06
You go into UEFI settings, usually with Dell it is f2, boot options are f12 to choose to boot USB flash drive.
With Dell you need fast boot off as that assumes no system changes and drive settings changed from RAID or Intel RST to AHCI.

These are my partitions on one system, but I have multiple versions of Ubuntu installed, some now obsolete, but not yet overwritten with a newer version.

[https://ubuntuforums.org/showthread.php?t=2437535&p=13934695#post13934695](https://ubuntuforums.org/showthread.php?t=2437535&p=13934695#post13934695)

ESP is FAT32 partition
/ is ext4 partition
and if you have separate /home it is ext4 and larger than /. 
Some advanced users may use other Linux formats but best to stay with the current standard ext4 format.

Dell settings are often common across many models. Several examples & links in the link below on Dell specific settings.

---

### Post by pbear42 on 2020-08-06
> **dev197 said:**
> ... manual partition is my only choice ...
That's odd.  There should be two choices: Erase disk and Manual partitioning.  Just checked in VBox (I have the ISO, as I installed Lubuntu to a multi-boot USB hard drive) and the option is there when I boot a live session and run the installer.  Have you read the [manual]("https://manual.lubuntu.me/stable/")?

---

