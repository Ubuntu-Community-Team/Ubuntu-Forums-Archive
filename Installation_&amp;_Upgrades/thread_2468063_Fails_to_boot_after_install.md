---
title: "Fails to boot after install"
date: 2021-10-17
forum: Installation &amp; Upgrades
---

### Post by gord-d on 2021-10-17
Any assistance is appreciated.  I have a ThinkStation E30 and I'm trying to install linux from a Ubuntu image on a USB stick.  I've tried the default, I've tried a complete repartition of the hard disk, but the result is always the same, the bios can't find an operating system.  I installed boot-repair and ran it, it didn't fix the problem, but it did generate this report: [https://paste.ubuntu.com/p/mnVvqHbmWQ/](https://paste.ubuntu.com/p/mnVvqHbmWQ/)

---

### Post by oldfred on 2021-10-17
It says grub installed correctly & ubuntu/grub is first in UEFI boot menu.
Make sure system is set to boot in UEFI mode, not CSM/Legacy/BIOS mode.

What video card/chip?
Specs say either Intel or several nVidia as options.

With single install, you do not normally get grub menu.
If you press Escape key right after Lenovo logo or UEFI/BIOS logo & just before grub menu would appear, do you then get grub menu.
You may have to try several times as timing is short. And if fast boot in UEFI settings is on, you may not even have time to press any key. 
If Fast Boot in UEFI is on, turn it off or do a full cold boot, so UEFI does a normal not fast boot.

Then can you boot second line in grub menu or recovery mode?

If nVidia, did you install proprietary drivers as part of install?

---

### Post by gord-d on 2021-10-18
Thankyou for the quick response.  System was set to UEFI, but still no joy.  In the live-boot, I checked to download software and updates (hopefully, that means getting the right video drivers.  Either way I think it is moot as the bios isn't finding anything to boot.  To slow things down, not only is fast-boot turned off, I added a 10 second delay in the bios to give the hard disk time to spin up (and give me time to react).

Unfortunately, my window of opportunity to spend time on this project has passed and I won't have a couple of days to look at this again until December.

---

### Post by gm310509 on 2022-04-26
FWIW, I had heaps of problems installing (i've spent all day trying to get a bootable installation).

I had I/O errors - I don't know why, but didn't have these with a previous OS installation on the same PC. The latest version of balanaEtcher didn't create a Ubuntu bootable USB for me (but does create a bootable USB for OpenSuSe), in the end, I used the latests rufus to create the USB (which worked).

The final problem after installation was rebooting to a "no operating system found" error. Thanks to this post, I noted that my laptop was in "legacy" boot mode. Changing to UEFI **did** fix this particular issue. So I just wanted to add support for that check (I don't know if it is possible, I suspect not, but it would be great if the installer could detect that issue).

---

