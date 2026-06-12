---
title: "ubuntu usb/cd"
date: 2013-02-20
forum: Installation &amp; Upgrades
---

### Post by geeklinux on 2013-02-20
Hi

I haven't used ubuntu now for several year, but just few days ago i started picking it up again, but i have few problem, that i did not have few years ago,

The first problem i have is, when i make a bootable cd with ubuntu it wont boot, i have tried everything i can, still same problem, did try that in defferent computer still same problem.

The secod problem i have is usb, same problem i do get.
 I have used those software that people do recommend here in forum, still getting same problem almost, " cant find the image " etc ...

i do have windows 8 installed, will that be a problem.

Thanks for any help guys, if you want to know more just pm me or write it here . ...

---

### Post by oldfred on 2013-02-20
Welcome to the forums.

Windows 8 is a whole different way. It uses UEFI not BIOS and uses gpt partitioning not the old MBR(msdos) partitioning.

Did you download the 64 bit version? Have you turned secure boot off and fast boot off?

What system is it as some have major issues. Also what video and is it an UltraBook or with a small SSD?

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
> As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

    
       Some Toshiba's will not boot.
 they managed to leave the signing key out of the database that's used to validate binaries
Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)
    
       UEFI boot live-usb bricks SAMSUNG 530U3C,np700z5c laptop - fix released
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)
[http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html](http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html)
The problem also appears to affect Ubuntu 12.10 and other Samsung models. The Ubuntu bug report includes posts from users reporting that the problem also affects 300E5C, NP700Z5C, NP700Z7C and NP900X4C series laptops.

    
But many systems work, some easily, some with a little effort and some not so much.

---

