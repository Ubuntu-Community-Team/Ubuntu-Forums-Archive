---
title: "Attention to anyone who installs Ubuntu 10.04 via USB stick!"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Motjida on 2010-04-30
Hi all,

I've seen quite a few threads on this now, and I had the problem myself.

Basically, you can boot into LiveCD and there are no problems during installation, but when you reboot (and remove the USB stick) you'll run into a black/blue screen (just after the BIOS has loaded), where a _ will flicker forever in the top left corner. In short... no boot!

I found that when you install Ubuntu 10.04 (maybe not all versions do this, but the desktop versions do), via an USB stick, the bootloader (GRUB) defaults to being installed on the USB stick and NOT the local HDD.

As an example: When I did my installation, the local HDD got assigned to /dev/sdb/ while the USB stick got assigned to /dev/sda/. And surely enough the bootloader is being installed to /dev/sda/.

If above is the case for you, please make sure that on Step 7 (Where you click Install), click 'Advanced' and remap the bootloader to match the local HDD (in my case /dev/sdb/).

I hope this helps some people out there, as it tied me up for hours and was driving me nuts :)

/Mot

---

### Post by snevs on 2010-08-13
Confirmed.

I was struggling for almost 8 hours to figure out a way to install Ubuntu 10.04 from a USB stick onto a Toshiba T110-10x (Windows 7 pre-installed).

First I was getting kernel panics because of the WI-FI card (incompatible drivers - wifi card should be disabled from BIOS first).

After re-installing/copying the installation kit to the stick, I finally went to the BIOS and disabled the WI-FI card. 
Then, I had no problem with Ubuntu, except that the grub was installed to the [COLOR=Red]**sda drive** which is the USB STICK[/COLOR], and the WI-FI card not working at all who would think that it will be recognized as sda instead of sdb?
(sdb is the hard drive and not any other secondary drive attached to the system)

I managed to get Ubuntu installed and working properly after re-installing, because after an update, it changed the grub to some other place else.

I'd suggest to install from the USB stick and know your drives, be careful and read every message that shows up on the screen.

Cheers mates.

:razz:

---

