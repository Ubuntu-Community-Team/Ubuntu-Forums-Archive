---
title: "Unable to boot after installing ona Lenovo B570"
date: 2014-04-08
forum: Installation &amp; Upgrades
---

### Post by coversnail on 2014-04-08
I've run into a problem after installing Ubuntu 13.10 on my Lenovo B570 in that it fails to boot, and I get this error message:

Could not open "\EFI\BOOT\fallback.efi": 14
Failed to open \EFI\BOOT\grubx64.efi - 80000000000000000E
Failed to load image
Failed to open \EFI\BOOT\MokManager.efi
Failed to load image

[http://imgur.com/DyUCq6E.jpg](http://imgur.com/DyUCq6E.jpg)

I tried using Boot-Repair which hasn't helped, this is the boot info summary:

[http://paste.ubuntu.com/7221670/](http://paste.ubuntu.com/7221670/)

I can still boot into a LiveUSB session, and also can use Super Grub disk allows me to boot into the installed version of Ubuntu. I have checked other threads based on this model but haven't found a solution which works here. If anyone could help I'd be very grateful

Many thank

---

### Post by oldfred on 2014-04-08
You are not showing a ubuntu UEFI entry - see line 735 thru 744. And default seems to be setup?

Reported as a Mac issue but also Lenovo users have also said same issue. 
 Could not open "\EFI\BOOT\fallback.efi"
[https://bugs.launchpad.net/ubuntu/+bug/1241824](https://bugs.launchpad.net/ubuntu/+bug/1241824)

Do you have secure boot on? Best to have it off.
You also have a Windows boot loader in the protective MBR, do not use BIOS/CSM/Legacy boot as that will not boot anything.

---

### Post by coversnail on 2014-04-08
> **oldfred said:**
> You are not showing a ubuntu UEFI entry - see line 735 thru 744. And default seems to be setup?

Reported as a Mac issue but also Lenovo users have also said same issue. 
 Could not open "\EFI\BOOT\fallback.efi"
[https://bugs.launchpad.net/ubuntu/+bug/1241824](https://bugs.launchpad.net/ubuntu/+bug/1241824)

Do you have secure boot on? Best to have it off.
You also have a Windows boot loader in the protective MBR, do not use BIOS/CSM/Legacy boot as that will not boot anything.

thanks for the reply. I'm not sure how I would change the boot order or why there is no Ubuntu UEFI entry

That bug report suggests that > copy /EFI/ubuntu/grubx64.efi to /EFI/BOOT/fallback.efi may solve the problem but I'm also not sure how to do that.

The laptop doesn't have secure boot I'm pretty sure, it was a Windows 7 model, these are the option available in the BIOS menus
[http://imgur.com/rA9tLB8](http://imgur.com/rA9tLB8)
[http://imgur.com/5onRDMJ](http://imgur.com/5onRDMJ)
[http://imgur.com/CrTba8a](http://imgur.com/CrTba8a)
[http://imgur.com/E8eYdEE](http://imgur.com/E8eYdEE)
I don't think the legacy option applies to booting from the HDD, when it is deactivated my Live USB no longer boots.

Thank you for helping

---

### Post by oldfred on 2014-04-08
In that bug report was this suggestion.

Secure boot:
 copy /EFI/ubuntu/shimx64.efi to /EFI/BOOT/fallback.efi
copy /EFI/ubuntu/grubx64.efi to /EFI/BOOT/grubx64.efi
 Nonsecure boot:
copy /EFI/ubuntu/grubx64.efi to /EFI/BOOT/fallback.efi

Someone posted this:

 How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)

      
 Another lenovo solution copy grubx64.efi to bootx64.efi & boot hard drive not anyother entry
[http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470](http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470)

---

