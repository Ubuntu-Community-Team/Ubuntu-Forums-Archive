---
title: "Ubuntu 13.04 on Dell XPS 14"
date: 2013-09-17
forum: Installation &amp; Upgrades
---

### Post by cryptoparrot on 2013-09-17
Hi all,     I'm having an issue installing Ubuntu on a dell XPS 14. 

   Steps so far:    
Turned off secure boot in BIOS   
Turned off the Intel Rapid Storage and returned SATA operation to AHCI    
Shrunk the Windows 8 partition by 100GB    
Booted Ubuntu from USB      

It didn't detect the presence of the Windows 8 OS on installation, so I had to manually partition the free space I had created. I added 40GB for Home, 55GB for / and 4GB of Swap. The installation was successful and upon boot I'm presented with the GRUB menu, which only offers me Ubuntu (No windows is listed). If I try and boot into Ubuntu I just hang on the purple background screen and nothing happens. I've managed to boot back into Windows by selecting boot options on startup and selecting the Windows Boot Manager from the UEFI boot menu.   In Windows diskmgmt.msc it almost seems like the partitions haven't been written to. I don't know if this is normal but the partitions for /home and / are listed as RAW. 

    Any ideas as to what I can do to fix this? If you need anymore info then please ask and I'll do my best to provide it.      

Thanks

---

### Post by ajgreeny on 2013-09-17
How did you shrink the windows partition?
How did you make the partitions for ubuntu?  If you did that in windows disk management you may have dynamic partitions which Linux is unable to use.

You should always shrink Windows using the windows disk management tool, and then boot into windows and run chkdisk to make sure everything is OK.
Never make partitions for linux using windows, but leave the space unallocated.

Tell us in more detail what exactly you did and we may be able to help more.

---

### Post by cryptoparrot on 2013-09-18
Hi, 

Thanks for the reply. 

I shrank the system volume in Windows using Parted Magic. I initially tried this in Windows but it threw errors about the disk not having enough space to Shrink by 100GB (Which it definitely did). I thought this may be an error with a system file in use that needed to be moved, so I went with a live boot USB. I left this as unallocated space. After this I logged back into Windows and everything was working perfectly, with 100GB of free unallocated space at the end of the disk. 

I then booted the Ubuntu installer, it didn't detect my Windows 8 install so I clicked 'Do something else' and partitioned the disks manually. I found the freespace I had created and chopped it into:

 40GB ext4 Primary - /home
56GB ext4 Primary - /
4GB swap

The installer seemed to run with no issues, when the system rebooted I was presented with the GRUB menu. In the menu I could only boot from Ubuntu (and the other utilities that GRUB comes with as standard) and I couldn't see my Windows 8 boot option. When I selected the Ubuntu option I was presented with a purple screen, where the system just hangs. 

I could get back into my Windows 8 install by selecting the boot menu in UEFI and selecting the Windows boot manager option. 

I the

---

### Post by oldfred on 2013-09-18
Did you install in BIOS mode not UEFI mode?

How you boot install media is how it installs. Or boot in BIOS mode installs in BIOS mode.
 Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Boot-Repair can convert a BIOS install to UEFI by uninstalling grub-pc and installing grub-efi. May be best to see details.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

Did you turn off fast boot or hibernation. That is one reason the installer will not see the Windows partition. The other is if this is an Ultrabook, it uses Intel SRT which has RAID meta data on drive.

Dell seems very similar across models, main difference is screen size and whether Ultrabook or not.
 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell UltraBook - Instructions & Details in Post #15 & 16 Devine Shine
[http://ubuntuforums.org/showthread.php?t=2144853](http://ubuntuforums.org/showthread.php?t=2144853)
Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)
Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)
Dell 14z used Dell Recovery and Refind
[http://ubuntuforums.org/showthread.php?t=2125397](http://ubuntuforums.org/showthread.php?t=2125397)
 HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
Do not understand why flash cache is required, just install to SSD?
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)

---

