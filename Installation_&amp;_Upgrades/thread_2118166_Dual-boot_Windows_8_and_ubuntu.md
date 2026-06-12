---
title: "Dual-boot Windows 8 and ubuntu"
date: 2013-02-20
forum: Installation &amp; Upgrades
---

### Post by Jbouska on 2013-02-20
Hello Everyone!

I have a serious problem over here.  I recently purchased a new ACER-V3 that came pre-loaded with windows 8.  I completed my dual-boot, unfortunately I loaded Ubuntu 10.10 on accident.  My internet works fine on the windows side of things, but not at all on the ubuntu side.  I'm trying to update to a 12.04.02 LTS or 12.10, but cannot access the internet to do so.  I have since made disks for 12.04.02 LTS , 12.10, and 12.10 alt but cannot get them to work.  Please help!!!

---

### Post by oldfred on 2013-02-20
Welcome to the forums.

I am surprised you even got 10.10 to install. You must have installed in BIOS/legacy/CSM mode not UEFI.

When you say will not boot, does it start and then a video issue or not even start. You do have to have the 64 bit version.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
> As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

    
       Acer V5-571P-6815 secure boot off worked
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

---

### Post by Jbouska on 2013-02-20
I'm surprised that it loaded too...I can't access the internet though to get the files I need to update.  Is there anyway I can troubleshoot the drivers?

i ran iwconfig and it came back

lo no wireless extensions

---

### Post by oldfred on 2013-02-20
Many wireless need drivers, so you have to use the Ethernet hard wired connection to get on line to download wireless drivers. Almost all Ethernet chip drivers are included, but there are exceptions.  There may be a way to off line download and install, but I have not followed those issues as my systems just work.

If you want just info on Internet issues start a new thread with that in the title and post details of your hardware.

or search forum based on your model chip.
       Using google is often better than the forums search function.
Just append site:ubuntuforums.org to your search term
[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

