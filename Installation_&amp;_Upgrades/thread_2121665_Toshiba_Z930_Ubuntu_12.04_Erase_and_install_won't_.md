---
title: "Toshiba Z930 Ubuntu 12.04 Erase and install won't boot."
date: 2013-03-02
forum: Installation &amp; Upgrades
---

### Post by DaKellyFella on 2013-03-02
Hi guys/gals,

So I've had a browse around and haven't found any other posts similar to my situation. I've tried to do an overwriting install (erase hard driver and install Ubuntu) of Ubuntu 12.04 (64 bit) on my Toshiba Z930 but it won't boot passed bios. I never see Grub, only a Toshiba logo.

I have disabled secure boot in the bios (I did so it would install correctly) but still no joy. All other settings are default (boot order etc). 

Have I done something wrong? Sorry if its obvious!

Thank you.

---

### Post by oldfred on 2013-03-02
If this is a new UEFI system. But see issues below. I might make sure you have newest UEFI/BIOS version. And some systems have integrated Windows & UEFI, so I would not totally erase Windows until issues are resolved.

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

      
  [SOLVED] Can't install Windows 8 & Ubuntu in Toshiba Portege Z930 with explanation how by OP feb 2013
[http://ubuntuforums.org/showthread.php?t=2114290](http://ubuntuforums.org/showthread.php?t=2114290)

      Samsung, Lenovo & Toshiba UEFI issues
[http://mjg59.dreamwidth.org/22028.html](http://mjg59.dreamwidth.org/22028.html)

Some Toshiba's will not boot.
 they managed to leave the signing key out of the database that's used to validate binaries

---

### Post by DaKellyFella on 2013-03-02
OK I'll give those links a read. Unfortunatelty I've already erased Windows from the disk and there's nothing on it except an Ubuntu installation that I can't boot. I don't know how messed it will be...

Thanks!

---

### Post by oldfred on 2013-03-02
This post this and run Boot-Repair.
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by DaKellyFella on 2013-03-03
OK OldFred I ran boot-repair and it worked. Can't believe it was that easy. I guess I just panicked.

Thanks for all your help.

---

### Post by oldfred on 2013-03-03
Glad that worked. :)

Boot-Repair usually works and in those cases it needs more help it creates the BootInfo report with lots of details on your system.

---

