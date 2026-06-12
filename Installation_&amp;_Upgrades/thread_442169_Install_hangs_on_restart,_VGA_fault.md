---
title: "Install hangs on restart, VGA fault"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by doclamb on 2007-05-13
Hi, from a novice at Linux and Ubuntu.
My installation of Ubuntu 7.04 desktop hangs on restart - nothing happens pressing ENTER after removing the live CD. I have tried installing on a third harddisk (after a raid-strpie and my windows hd - all SATA. Cold reboot renders probably a fault in GRUB and I can't load Ubuntu, but Windows XP runs normally. I then tried disengaging the other disks and the same hang at restart happens. However I seem to load Ubuntu according to the sounds, but the video mode is not supported and the screen is black.
I run a X2 processor, Asus SLI Nvidia motherboard and Asus PCIe graphics. In Windows I run a dual display (identical monitors) and have monitors plugged in the DVI and VGA output. The default VGA video mode does not work from the live CD, but some other resolutions work on both screens - and other only shows correctly on the DVI-connected monitor. It doesn't seem possible to choose a video mode for the installation and probably the default VGA mode is chosen - which doesn't work on my system. What can I do?
Regards from Jan Lambrecht

---

### Post by x64Jimbo on 2007-05-13
The system hanging on CD eject is not uncommon. But it also doesn't mean that the installation did not work. What option did you choose for the GRUB installation? It **should** be installed on the MBR of the first booted HDD.

---

### Post by doclamb on 2007-05-13
Thank You very much for your reply.
I chose GRUB install on the third disk  with the Ubuntu installation (hd2) in order to avoid tinkering the MBR. I set the bootdisk to this disk in BIOS.That might be the trouble with booting after install. I have read several threads about avoiding this.
My challenge is now not GRUB, but the not supported VGA resolution. Is there a way to change this in the installed files - when booting from the live CD (with an appropriate resolution)?
I'll take the GRUB challenge later after replugging the other HD's.
With regards

---

### Post by x64Jimbo on 2007-05-14
Re: graphics trouble
have you installed your video card driver?

---

