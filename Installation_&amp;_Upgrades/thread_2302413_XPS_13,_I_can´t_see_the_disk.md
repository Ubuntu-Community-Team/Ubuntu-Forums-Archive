---
title: "XPS 13, I can´t see the disk"
date: 2015-11-10
forum: Installation &amp; Upgrades
---

### Post by mustermark on 2015-11-10
Hi everyone,
I´ve tried to install Ubuntu (either 14.04 or 15.10) on a new XPS 13 (9350). I've read a couple of guides online for the 9343 version of the laptop (they are both essentially the same, just an update of the processor, I think), like these ones:
[http://hgdev.co/install-ubuntu-15-10-on-the-dell-xps-13-9343-2015-a-complete-guide/](http://hgdev.co/install-ubuntu-15-10-on-the-dell-xps-13-9343-2015-a-complete-guide/)
[http://forthescience.org/blog/2015/03/20/installing_ubuntu_14_04_on_the_new_dell_xps_13/](http://forthescience.org/blog/2015/03/20/installing_ubuntu_14_04_on_the_new_dell_xps_13/)

They all suggest a relatively straightforward intallation, just a couple of fixes of the wifi and so. However, when I've tried to do it the installation does not detect the disk. I've used a startup disk of 15.10 or 14.04 generated with a machine with 12.04 and tried both booting live or installing on the fly. In either case the only disk detected is the usb key. I can´t see the hard disk on gparted either. I have not found any reference to this problem, any idea? 

Thanks a lot!

---

### Post by TheFu on 2015-11-10
I don't know anything specific, but recall there was something in the release notes for that model of Dell. Have you read the release notes?

---

### Post by mustermark on 2015-11-10
> **TheFu said:**
> I don't know anything specific, but recall there was something in the release notes for that model of Dell. Have you read the release notes?

Thanks for pointing that out, but the only thing that I see in the release notes is that the "wipe whole disk and install" option deletes also de EFI partition. In my case I don't even get to that point since the installation only sees the usb key partition and not the laptop disk!

---

### Post by TheFu on 2015-11-10
Does the BIOS have  "Win7 mode" that can be enabled or a "Windows8 mode" that can be disabled?  Been seeing this on newer laptops, unrelated to SecureBoot and the legacy BIOS mode selections.
I've seen the pre-loaded Ubuntu XPS 13 with the 4K display. Amazing kit, but I don't have $1300+ to spend.  ;(

I'm just guessing here.

You've probably already seen the Ubuntu UEFI guide. [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) so this is for lurkers.  Maybe oldfred will join with some wisdom?

---

### Post by mustermark on 2015-11-10
> **TheFu said:**
> Does the BIOS have  "Win7 mode" that can be enabled or a "Windows8 mode" that can be disabled?
Nope, I can't see anything like that. And, if I understand correctly, if I want to keep win 10 I'm forced to use UEFI. 

> **TheFu said:**
> I've seen the pre-loaded Ubuntu XPS 13 with the 4K display. Amazing kit, but I don't have $1300+ to spend.  ;(
Well, I opted for the slightly more humble FHD version with win10, thinking that installing ubuntu was going to be straightforward. It seems I was wrong ...

> **TheFu said:**
> You've probably already seen the Ubuntu UEFI guide. [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) so this is for lurkers.  Maybe oldfred will join with some wisdom?
I already tried disabling the RAID mode and the Fastboot, but nothing changed.

---

### Post by K3N8 on 2016-06-24
You need to disable RAID in the BIOS.

---

### Post by chesty2 on 2016-06-24
> **K3N8 said:**
> You need to disable RAID in the BIOS.

i just did this 2 hours ago and then i see this post. spooky.

yes, the storage controller will be set to raid, select ahci instead.

if you're dual booting, windows will no longer boot.
start up windows in safe mode and it will fix itself.

---

