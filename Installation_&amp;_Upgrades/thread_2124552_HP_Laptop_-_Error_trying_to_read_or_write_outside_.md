---
title: "HP Laptop - Error trying to read or write outside of hd0. Partitions?"
date: 2013-03-11
forum: Installation &amp; Upgrades
---

### Post by cyberguru on 2013-03-11
Hi all,
First time posting after reading the forums for a long time, looking at posts from other HP-suffering would-be Ubuntu users.
I have a HP DV6 laptop with a 750GB HD, Intel i7 and 6GB RAM. I downloaded Ubuntu 64bit and started to install it on my laptop. First issue was that there are 4 primary partitions on the laptop hard disk. Solved that by deleting the small HP_SUPPORT partition (created the HP restore DVD's and also a Win7 repair disk before hand, and I even have a Clonezilla image of the entire hard disk as well).
I used gparted and created about 120GB empty space on the hard disk; partitions go:
[LIST=1]
[*]HP Boot (200MB? Cant remember exactly)
[*]Win7 (~600GB, cant remember precisely)
[*]~120GB of free space.
[*]HP Recovery (20GB, can be deleted using HP utility)
[*]~200MB of free space where HP SUpport partition was
[/LIST]

I boot the Ubuntu disc and when it comes to setting up partitions, I choose "Something else" and then create ~40GB for '/', 60GB for '/Home' and then a little over 6GB as swap. '/' and /home are ext4 formatted.
Ubuntu goes off happy with its new home, installs ok and also adds boot options for my old Win7 system (three options, one for Booting, one that doesnt work (I think the old Win7 OS needs to boot from the first partition, not the OS partition) and even one for the recovery option).
The problem is that I have issues booting into Ubuntu. The most frequent error is "trying to read or write outside of hd0" or similar (cant remember the exact wording but it does say hd0). I have also seen some kernel panic's and a few "You must load kernel first" messages.
I can boot and use a liveCD of Ubuntu with no problems. I have tried deleting the install and starting again but sooner or later I get the same problem. Sometimes it starts with no problems, most of the time I get one or more of the above errors.
In Ubuntu, I have done "sudo fdisk -l" and see all the partitions, and see a warning about sda4 not starting on physical boundary (again, cant remember the exact error but I will put the output in here if it will help anyone).
I reccall in the olden days that any booting OS must be inside the first 300 or so gig on the disk. Ubuntu is living above the 5- or 600GIG area of my HD.
I have even tried Linux Mint 14 and get the same issue after a reboot. Could my disk have errors? Any tools you can get me to run that might help diagnose the issue?

Thanks in advance for the help.

---

### Post by oldfred on 2013-03-11
We have seen some systems with very large / (root) partitions or partitions very high on drive that have issues. It is somewhat like the very old BIOS limits but is in newer systems.

Do you have BIOS set for AHCI not IDE. Windows may need AHCI drivers installed before you change if it does not have drivers already installed.

Some create a small Linux/boot partition somewhere inside the first 100GB of system. But with Widows using all the space it can be difficult to find that space.

May be best to see details.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers)

 History of BIOS and IDE limits
[http://tldp.org/HOWTO/Large-Disk-HOWTO-4.html](http://tldp.org/HOWTO/Large-Disk-HOWTO-4.html)
Out of disk error add to grub install disk-module=ata or use Boot-Repair ATA Disk support
HOWTO: dualboot on big disk (BIOS limitations)
[https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk](https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk)
[http://ubuntuforums.org/showthread.php?t=1998257](http://ubuntuforums.org/showthread.php?t=1998257)
Large external drive still needed /boot at beginning:
[http://ubuntuforums.org/showthread.php?t=1888497](http://ubuntuforums.org/showthread.php?t=1888497)

   It was in the BIOS. Under Onboard Devices Settings, the SATA Mode was set to SATA. I changed it to AHCI. Then another  showed up in the BIOS that stated "Change the AHCI DID for Linux to Enabled. I booted to win7 and it loaded some new drivers. I booted to Gpart and glory be there were my hard drives.

---

