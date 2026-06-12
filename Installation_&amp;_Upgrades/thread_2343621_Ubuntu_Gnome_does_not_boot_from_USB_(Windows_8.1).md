---
title: "Ubuntu Gnome does not boot from USB (Windows 8.1)"
date: 2016-11-17
forum: Installation &amp; Upgrades
---

### Post by inkheart2 on 2016-11-17
Hello,

I am pretty green when it comes to Linux, but I wanted to try the Ubuntu Gnome (from what I read it's the best for touch devices) on my Windows 8.1 32-bit tablet to see how the two system stack up.

I downloaded the Ubuntu Gnome 16.04 32-bit and created a bootable USB with Rufus.

I disabled the fast and secure boot and selected the USB in the booting order as first.

When I power the PC on the USB is visible in the boot menu and when I select it seems to be trying to run it (a black screen appears with a cursor in the top left corner) but then it boots Windows instead.

As far as I know my PC is UEFI based which means GPT partition scheme. But when making the bootable USB in Rufus I can only use the MBR option, because when I select the GPT I get an error saying that only EFI bootable ISO images are supported (does that mean I need a different ISO? There are no EFI or no EFI ISOs on the Ubuntu Gnome website).

I hope this makes some sense. 

Can someone tell me if I'm doing something wrong?

---

### Post by ubfan1 on 2016-11-17
You may be trying to boot a 32 bit UEFI firmware, which even the 32 bit install media doesn't do (look for a /Boot/bootia32.efi as well as the 64 bit bootx64.efi).  There are such 32 bit bootloaders around, but I have no experience with them.  search this forum and the askubuntu site.

---

### Post by oldfred on 2016-11-17
And only the 64 bit Ubuntu version is UEFI capable. 
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    
Is your tablet one of those with 32 bit UEFI but 64 bit system?

---

