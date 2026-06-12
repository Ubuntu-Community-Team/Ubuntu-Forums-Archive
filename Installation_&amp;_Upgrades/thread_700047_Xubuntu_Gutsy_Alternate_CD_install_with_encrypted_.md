---
title: "Xubuntu Gutsy Alternate CD install with encrypted volume"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by T_Beermonster on 2008-02-18
I am using the Xubuntu alternate CD (x86) to try to install on an external USB mounted 16Gb flash drive that I can then take with me and use on other machines as and when the need arises. Obviously being a portable drive encryption is necessary and though I run an AMD64 machine I chose the x86 version to ensure maximum compatibility.
To avoid any confusion during the install I disconnected my internal hard drive.

The text installation all seems to go perfectly smoothly setting up an unencrypted /boot partition LVM and encrypted root (No swap), installing the basic system, installing the full system and installing grub. The installation completes and the CD is ejected before reboot.

On reboot GRUB gets to stage 1.5 and returns Error 2.

Error2 is unhelpfully described as "Selected disk doesn't exist"
"This error is returned if the device part of a device- or full filename refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system."

This I suppose tells me what the problem is but gives me no indication of which device doesnt exist. I'm going to guess that it is the encrypted root, but it is only a guess since it could also be something to do with it being a USB device (or well it could be looking for a flying monkey for all I know).

I had read in various places that removing all "splash" entries from /grub/menu.lst could help. It seemed unlikely since GRUB didnt get far enough to splash but I gave it a shot and as expected got no joy.

Does anyone have any experience of successfully installing to an encrypted root? Can anyone offer any suggestions as to any solutions?

---

