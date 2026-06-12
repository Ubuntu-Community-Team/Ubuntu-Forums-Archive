---
title: "Trouble Booting and Running from USB Flash Drive"
date: 2016-10-15
forum: Installation &amp; Upgrades
---

### Post by mikea08 on 2016-10-15
Hi, I've searched around quite a bit and haven't seen anything too close to what I'm experiencing, so I hope this hasn't been asked before.

My goal is to run the full version of Ubuntu 16.04.1 LTS from a 32 GB flash drive on a system that is currently running Windows 10 from its internal HDD (which I want to keep).  
Specs:

HP ZBook 15 G3
Intel Core i7 6700HQ @ 2.60 GHz
16 GB RAM
UEFI N81 Version 01.08

I used Rufus to create a bootable USB Ubuntu which boots up and runs perfectly.  I then used it to install Ubuntu to my separate 32 GB flash drive which I partitioned with 2 GB for swap and the rest Ext4 for the install and put the bootloader on the device itself.  When I selected to boot from USB in my UEFI, it just flashed a black screen for a second and reloaded the boot selection screen.  From that install on, "UEFI Ubuntu" has been persistent as a boot option even when I have no Ubuntu USB's installed.  I did not install the bootloader on my Windows EFI partition so I don't know why it is there.  When I select it without a Ubuntu USB, grub loads but "minimal bash-like line editing is supported ubuntu" is displayed.  

I then reformatted and reinstalled Ubuntu on the same flash drive, but this time I added a 2 GB EFI partition after reading about it some more and installed the bootloader there.  Now when I restart, the USB is not recognized by the UEFI.  I found that if I boot the Live Ubuntu session and mount the full version flash drive and then restart, the UEFI does recognize it.  When I select to boot from the full version flash drive, it just flashes black and reloads the selection screen again like before, however, grub will load without issue if I select the persistent "UEFI Ubuntu" boot option.  I then select to load Ubuntu (not "Try Ubuntu" so I know the full version is booting) with mixed results.  The first time, I just sat with a black screen for about 10 minutes and had message with something like "Ubuntu booted with issues" and the keyboard/touchpad would not register any input.  The next time I booted it, it loaded almost instantly and seemed to be working ok although super slowly which I just thought was because it was on USB.  Now I can't get it to load at all though.

I would imagine I'm just not installing it correctly somehow since the Live session works perfectly.  Perhaps the Ubuntu bootloader that somehow got installed permanently is interfering with the USB bootloader, but I don't know how to get rid of it.

Any help getting the full version to run without affecting Windows and internal disks would be greatly appreciated.  Thanks!

---

### Post by oldfred on 2016-10-15
I have yet to find a version of grub that during install will go anyplace other than to drive seen as sda.
You can manually install grub to any drive, but have to specify many options and then manually maintain.

I just copy ESP entry for /EFI/ubuntu from sda to external flash drive's ESP. Then copy /EFI/ubuntu/shimx64.efi to /EFI/Boot. Then rename it to bootx64.efi as all external devices only boot in UEFI mode from an ESP entry of /EFI/Boot/bootx64.efi.
Version of grub that we copy is hard coded to find other parts of grub in /EFI/ubuntu, so both copies must be done.
The standard installer has a smaller version of grub also as /EFI/Boot/bootx64.efi, but that only has parts required to boot installer.

Some more info in link in my signature.

This user documented it a bit more. Seems ok, but I think he does an extra copy or two to /EFI, but I plan on a new reinstall of 16.10 to flash drive and will verify all his details.
[https://ubuntuforums.org/showthread.php?t=2338836](https://ubuntuforums.org/showthread.php?t=2338836)

---

