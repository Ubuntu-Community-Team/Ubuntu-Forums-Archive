---
title: "Drive space allocation while installing ubuntu 12.10 alongside windows 8"
date: 2013-04-16
forum: Installation &amp; Upgrades
---

### Post by scimas on 2013-04-16
I have windows 8 installed. I downloaded the 64bit ubuntu 12.10 iso file, created a bootable usb and chose try ubuntu. Now I am trying to install ubuntu. I chose the 'install ubuntu alongside windows 8' option. It took me to the page where I have to move the slider to decide the disk allocation.
My 1st question: My HDD is 500 GB, but it only shows me 10 GB and 4.8GB (I suppose 10GB is windows 8 and 4.8GB is ubuntu). Why so?
My 2nd query: Why can't I move the slider? I am trying to move the slider to increase the space for ubuntu, but it won't move.

Thanks for any help.

---

### Post by oldfred on 2013-04-16
Is this an install of Windows 8 that you did with BIOS/MBR, or pre-installed with UEFI/gpt and secure boot issues.

Either way you should use Windows disk tools to shrink Windows and reboot a couple of times to let it run chkdsk and make its repairs to its new size. Do not create new partitions with Windows as it may convert to dynamic which does not work with Linux.

If MBR(msdos) have you used all 4 primary partitions?
Post this from live installer:

       sudo parted /dev/sda unit s print

---

### Post by scimas on 2013-04-16
Windows 8 is not preinstalled. My PC was preinstalled with win7 which I then upgraded to win8. I don't know whether its 'BIOS/MBR' or 'UEFI/gpt'. Althogh the usb started with UEFI (I used that option from from Boot Optiions). Secure Boot is disabled (I checked that in the BIOS).

Model: ATA WDC WD5000BPVT-7 (scsi)
Disk /dev/sda: 976773168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start      End         Size        Type     File system  Flags
 1      63s        80324s      80262s      primary  fat16        diag
 2      81920s     29044735s   28962816s   primary  ntfs         boot
 3      29044736s  976771071s  947726336s  primary  ntfs

---

### Post by oldfred on 2013-04-16
If your system has UEFI be sure to only boot in BIOS/Legacy/CSM not UEFI as you have BIOS/MBR.  The partition table list shows msdos which with Windows will only boot in BIOS mode. 

You should be able to shrink Windows and create a new extended partition and then inside the extended you can have many logical partitions.

If a new user the default of / (root) and swap equal to RAM in GiB (not GB) is fine. It you have lots of RAM and do not hibernate swap only needs to be 2GB, just to have some and that may never be used.

 Install options, Do not use erase entire drive unless that is really what you want.
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

