---
title: "Probability of Success for this Desktop - Linux Only Install"
date: 2018-07-22
forum: Installation &amp; Upgrades
---

### Post by Geoffrey_Arndt on 2018-07-22
Recently one of my friends at our local PC club requested that I install Ubuntu on her HP desktop.   It's not use able now because for the second time in a year she has some nasty malware - and she is tired of dealing with that and other complexities of Windows 10.   So she wants to nuke Windows entirely and run only Linux.

So, can I get some input as to the odds of a successful install on an HP desktop with these specs:

HP Envy750-177c
>   Intel I7 6700 cpu
>   Intel Integrated 530 Graphics
>   16 GiB DDR3L Ram
>   Realtek Network chipset (ethernet)
>   Odense Motherboard H110

I "think" the machine should be very Ubuntu friendly, but I've never installed to an _HP UEFI machine_.    If I change the UEFI/BIOS to "Legacy" mode and let the installer overwrite the whole disk, will I still need any of the UEFI elements on the HDD (like and EFI partition and modifying the HP Windows version of the bootloader)???   Will the Grub bootloader install as in the pre-UEFI days and just load Ubuntu?

Any feedback is appreciated.

---

### Post by TheFu on 2018-07-22
The system is plenty powerful.  The realtek might be an issue, or not.
I would stay with UEFI boot AND secureboot if you can. The security is real.

I think HP doesn't follow the UEFI standards, so you'll want to find the manual steps necessary post-1st-install boot to correct them.  You can find links to that data in these forums from Oldfred's posts.  Oldfred keeps a list of HP+UEFI links.  It isn't very complicated, just a few extra steps to it works like normal. You won't have issues following them.

---

### Post by Geoffrey_Arndt on 2018-07-22
Thanks TheFu . . . if we go ahead with the install my first preference will be to boot from USB-Stick with latest (18.04) and leave uefi/bios as is.

---

### Post by oldfred on 2018-07-22
HP will work in UEFI mode. 
Best to also update UEFI from HP. Some now seem to work better.
HP was one that violated UEFI spec that says NOT to use description as part of boot.

       HP UEFI boot order change with efibootmgr does not stick, but change in HP's UEFI does work
[https://ubuntuforums.org/showthread.php?t=2390309](https://ubuntuforums.org/showthread.php?t=2390309)
HP 11m reinstall Windows & dual boot with Ubuntu 16.04
[https://ubuntuforums.org/showthread.php?t=2389104](https://ubuntuforums.org/showthread.php?t=2389104)
Probook G4 470 Ubuntu works fine with UEFI and secure boot. 
[https://ubuntuforums.org/showthread.php?t=2381663](https://ubuntuforums.org/showthread.php?t=2381663) 
    
If totally erasing Windows, the typical work around is to use the description "Windows Boot Manager" but boot /EFI/ubuntu/shimx64.efi which is the UEFI Secure boot version of grub.

Other work arounds & details of basic install in UEFI mode in link below in my signature.

---

### Post by Geoffrey_Arndt on 2018-07-22
Thanks for the additional info Fred.   

It may be mid-August before I can get a chance to test that install (unless she calls a Windows repair service first to fix the malware . . . again).

---

