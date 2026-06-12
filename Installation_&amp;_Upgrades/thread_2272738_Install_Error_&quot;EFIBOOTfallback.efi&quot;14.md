---
title: "Install Error &quot;EFI/BOOT/fallback.efi&quot;14"
date: 2015-04-08
forum: Installation &amp; Upgrades
---

### Post by nick180 on 2015-04-08
System: Samsung RV-511-S01UK laptop (manufactured 2011)

i3 380M @2.53Ghz
6GB RAM
1GB dedicated VRAM Nvidia GeForce 315M
Samsung 850 EVO 250GB SSD

SSD is MBR partitioned and has Win 8.1 installed on C: drive and D: is empty and available to install Ubuntu to create a dual boot system

I have used unetbootin to create a USB (3.0 32GB San Disk Ultra) installer for Ubuntu.... (laptop only has USB 2.0 ports)

At boot the first message I get is Error "EFI/BOOT/fallback.efi"14 then it goes to the screen with the 4 options and defaults to "try without installing"

This takes me to the following:

[IMG][[IMG]http://s14.postimg.org/ec8kgx8el/DSC_9027.jpg[/IMG]]("http://postimg.org/image/ec8kgx8el/")[/IMG]


Unable to locate medium containing a live file system....?

Tried several downloads of ISO and checked MD5 all with same result.

My BIOS looks like this in the Advanced tab:

[IMG][[IMG]http://s14.postimg.org/wdrpeq2fh/DSC_9028.jpg[/IMG]]("http://postimg.org/image/wdrpeq2fh/")[/IMG]

At this point I had tried enabling the UEFI support and get same result


All help much appreciated

Nick

---

### Post by oldfred on 2015-04-08
If Windows is in BIOS with MBR partitioning, you must boot Ubuntu in BIOS/CSM mode or you will erase Windows. How you boot installer is how it installs.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

So turn off UEFI in UEFI. Have you updated UEFI/BIOS to latest version from Samsung? Especailly if from 2011, some systems had major issues with UEFI. But if in BIOS mode you should be ok.

I have this in my notes from about 2011/2012.

 If Samsung check model number as some can only be installed in legacy/CSM mode or computer may be bricked.
Kernel updates being released and Samsung needs to update UEFI/BIOS.
      
 UEFI boot live-usb bricks SAMSUNG 530U3C,np700z5c laptop - fix released
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)
[http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html](http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html)
[http://mjg59.dreamwidth.org/25091.html](http://mjg59.dreamwidth.org/25091.html)
The problem also appears to affect Ubuntu 12.10 and other Samsung models. The Ubuntu bug report includes posts from users reporting that the problem also affects 300E5C, NP700Z5C, NP700Z7C and NP900X4C series laptops.
[http://mjg59.dreamwidth.org/23554.html](http://mjg59.dreamwidth.org/23554.html)

    
So only boot in BIOS mode.

You also have nVidia. Is this an Ultrabook that switches or does it just boot with nVidia chip in control, not Intel? You may need boot parameters to boot installer and until you install nVidia proprietary drivers.

You cannot install Ubuntu to a Windows d: "drive" which really is just a partition. Linux only uses drive as a physically difference drive and partitions for the subdivision of a physical drive. Drives are sda, sdb etc and partitions are then sda1, sda2 etc.
And Linux cannot use NTFS format for an install, only LInux formats like ext4.

---

### Post by nick180 on 2015-04-08
No matter what I do.... even with the strange UEFI OS and legacy OS support button disabled... using a brand new out of the packet SSD plugged in so there is NO operating system installed .... the SSD is blank.... the installer keeps getting to the screen that tells me it can't locate any medium with a live file and hangs right there.

Laptop has latest BIOS from 27:11:2012

---

### Post by oldfred on 2015-04-08
The installer is loading?
Can you boot in live mode, not installer?
Does it show drive?
Does UEFI/BIOS show drive?
Do you have drive set as AHCI in UEFI? 
Was drive ever RAID? or other odd formats that might interfer with installer seeing it? Or orginally gpt and Windows did conversion to MBR? (Windows always does it wrong.)
Can you use gparted on live installer to see drive?

Post this:
sudo parted -l
sudo fdisk -lu

---

### Post by nick180 on 2015-04-09
Get this.... I decided to ditch my brand new 32GB San Disk Ultra USB 3.0.... and create an installer with an old 8GB USB 2.0.

Instant success.... even though I'd scanned the San disk for errors it seems there is something wrong with it.

BTW.... FYI....I set AHCI to auto.... and disabled UEFI support

Now I need to ask operational questions over on another section

cheers

---

