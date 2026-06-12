---
title: "Dual Booting Windows and 16.04 on a Dell XPS 13"
date: 2016-11-02
forum: Installation &amp; Upgrades
---

### Post by datrock on 2016-11-02
Hi,
When I run the ubuntu install after manually creating a /ext4 partition, a swap partitions and changing the bootloader install location to dev/nvme0n1p I still an error reading: "grub2 has failed to install on dev/nvme0n1p this is a fatal error." Windows came preinstalled on the machine in UEFI mode so I cannot change to Legacy boot mode. On the drive there is already a EFI partition however it contains windows boot manager. I have disabled secure boot, fast boot etc. My XPS is a 9350 if that helps.
Thanks :)

---

### Post by oldfred on 2016-11-02
Grub should install to the existing ESP - efi system partition. All UEFI boot installs use one ESP.

But some have had issues with grub installs to NVMe drives.

Do you have latest UEFI from Dell?

       Kernel 4.6 has Dell & Alienware improvements including 9350
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers)
Similar models

 Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241) 
      
 Dell support - Update on XPS 13/15 2016 Developer Edition availability
[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9)

---

### Post by datrock on 2016-11-04
Ok, so I updated my UEFI to the latest available. I tried a myriad of suggested bios settings, specified the efi partition of my drive for bootloader installation in ubuntu install menu. After one of the failed install I ran disk-repair on my live usb. Nothing worked still the exact same issue. I might try downloading an older iso that others have had success with then upgrading.

---

### Post by oldfred on 2016-11-04
Post link to Summary Report from Boot-Repair.

---

### Post by datrock on 2016-11-05
Hi Thanks for the help: [http://paste.ubuntu.com/23429972/](http://paste.ubuntu.com/23429972/)

---

### Post by oldfred on 2016-11-05
You must have Windows fast start up off. That is always on hibernation.
       Fast Start up off (always on hibernation)

> Windows is hibernated, refused to mount.
Failed to mount '/dev/nvme0n1p3': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions) 

    
Best to only use newest version. Many Dell changes are only in newest versions of Ubuntu.

---

### Post by datrock on 2016-11-05
Thanks again for the help. I disabled fast boot in Windows, ran the installer but got the same error. 
Here is the pastebinit from boot-repair: [http://paste.ubuntu.com/23431170/](http://paste.ubuntu.com/23431170/)

---

### Post by oldfred on 2016-11-05
Do not know where all the Dell lines are coming from. May be corruption somewhere?

       Must be unmounted, standard commands:
sudo dosfsck -t -a -w /dev/sdb1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)
But in your case drive is /dev/nvme0n1p1
So probably
sudo dosfsck -t -a -w /dev/nvme0n1p1

---

### Post by datrock on 2016-11-05
Thanks but I'm a newbie, do I run this just in a terminal on my live usb?

---

### Post by oldfred on 2016-11-05
Yes, but be sure not to click on that partition with file browser as that would mount it. Or make sure you unmount if you have mounted it.

---

