---
title: "Install Xubuntu (MBR, GPT, UEFI, partition issues)"
date: 2016-01-05
forum: Installation &amp; Upgrades
---

### Post by grcd84 on 2016-01-05
I need some help with installing Xubuntu 15.10 (single OS, _NOT_ dual-boot) on a Lenovo Ideapad S205 installed with a 128GB SSD.

The SSD previously had Windows 10 Home x64 installed (upgraded from Windows 7 x64 Home Premium) but I have formatted the drive entirely as I do not intend to return to Windows 10 in the near future. 

I tried the 'simple' 'delete everything' installation, with Ubuntu, Lubuntu and Xubuntu live USB installation media, but I always get a boot-loop (no OS is recognized) after being prompted to reboot. On an interesting side-note Elementary OS installs just fine (and boots from the disk), but it is not the distro I want.

I have tried using the boot-repair (automatic options set), but although it claims to have fixed the problem, nothing really happens and the laptop stays in a boot-loop. I am confused regarding GPT and MBR -- my laptop has very limited settings to change in the BIOS, and SecureBoot (or equivalent) is NOT available from the options! The only thing I can actually change is the boot order of devices, but nothing else.

I used gdisk to switch GPT to MBR, to no avail (and run boot-repair again). So, I would like advice on how to set-up this system:

Which partitions to create manually? 

Is there any other known method, if the common method fails? 

I am a complete noob, although I have some experience with installing Linux in the past (with no such problems).

The only thing I want is Xubuntu to boot from the SSD. No other hard drives installed, no other OS to boot. 

Edit: 

I gave it another try (no results).
Here are the partitions (all primary) I set-up:

dev/sda: gpt

dev/sda1 fat32 128.00MiB boot, esp
dev/sda2 ext4  21GB /
dev/sda3 ext4 91GB /home
dev/sda4 linux-swap 7GB

[COLOR=#000000]I have attached a pastebin report from disk-repair:[/COLOR]

[http://paste.ubuntu.com/14413264](http://paste.ubuntu.com/14413264)

Edit 1: In the disk-repair settings, I unticked 'Secureboot' or the equivalent setting. I believe this has made a difference, although I also changed other things so I cannot be certain if that did the trick or not...

Edit: 2 I have managed to fix my problem. I leave my most-recent configuration and pastebin report from disk-repair for others who may run into the same problem. Many thanks!

---

### Post by oldfred on 2016-01-05
I thought most systems would boot in the 35 year old BIOS/Legacy/CSM mode without issue.
But you do not have logical partitions is using gpt.
And Ubuntu can boot in either UEFI or BIOS mode from a gpt partitioned drive. But if UEFI you must have the ESP - efi system partition for UEFI boot or a unformatted  or 2 MB partition with the bios_grub flag. I normally have put both on all new gpt drives and only formatted new drives with gpt for last several years even when old system was BIOS only.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

Not sure if Lenovo is consistent across all models, but many vendors now are modifing UEFI to use description as part of UEFI boot. That is specially **not** allowed per UEFI spec. And of course only description that works is Windows. But if only installing Ubuntu we find we can just change the UEFI description from ubuntu to Windows and it will still boot ubuntu/grub's shim file without issue.
If dual booting with change the fallback/default drive entry to be grub's shim boot file and that works. So there are ways to get system to boot in UEFI mode also.

      
 Lenovo rename files
[http://ubuntuforums.org/showthread.php?t=2302170](http://ubuntuforums.org/showthread.php?t=2302170)
Lenovo Laptops there is NOVO button on left side
Lenovo S20-30 BIOS install only
[http://ubuntuforums.org/showthread.php?t=2277003](http://ubuntuforums.org/showthread.php?t=2277003)
T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)
    
If only Ubuntu, use efibootmgr to create Windows boot entry that really boots grub.
      
 **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

     

Starting point for partitions, I like to have several / (root) partitions and a data partition, but each user has to determine what they need or want.
      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 15-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by grcd84 on 2016-01-05
Edit: Solved! MANY thanks! :)

---

