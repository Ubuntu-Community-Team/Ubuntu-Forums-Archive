---
title: "Ubuntu Install freezing  on [drm] nouveau Raw DCB Entry 0"
date: 2012-03-03
forum: Installation &amp; Upgrades
---

### Post by parkej3 on 2012-03-03
Hi,

I've have tried multiple different versions of Ubuntu (11.10, 12.04), but when I try to install Ubuntu on my hard drive, it pauses when trying to read the Display Configuration Block. I completely wiped my hard drive and then tried a fresh install and am still getting the error.

Is this a hardware problem? Is is a BIOS issue?

Here are the lines of the install before the freeze:

VGA switcheroo: detected Optimus DSM method \ handle
nouveau: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[drm] nouveau: Detected an NVc0 generation card (0x0c4100a1)
[drm] nouveau: Attempting to lead BIOS image from PRAMIN
[drm] nouveau: ... appears to be valid
[drm] nouveau: BIT BIOS found
[drm] nouveau: Bios version 70.04.13.00
[drm] nouveau: TMDS table version 2.0
[drm] nouveau: Found Display Configuration Block version 4.0
[drm] nouveau: Raw DCB entry 0: 02000300 00000000

It freezes on that last line everytime.

Help please!

Many thanks in advance.

---

### Post by efflandt on 2012-03-03
What specific model Nvidia card do you have?

Are you using **nomodeset** kernel boot parameter?  I found that I had to use that in 11.10 even though I did not have to use that in 10.10 with the save nvidia driver version number.  Without nomodeset for 11.10 my monitor (HDTV) would go black with "no signal" after the grub menu.

---

### Post by MAFoElffen on 2012-03-03
> **parkej3 said:**
> VGA switcheroo: detected Optimus DSM method \ handle
nouveau: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[drm] nouveau: Detected an NVc0 generation card (0x0c4100a1)
[drm] nouveau: Attempting to lead BIOS image from PRAMIN
[drm] nouveau: ... appears to be valid
[drm] nouveau: BIT BIOS found
[drm] nouveau: Bios version 70.04.13.00
[drm] nouveau: TMDS table version 2.0
[drm] nouveau: Found Display Configuration Block version 4.0
[drm] nouveau: Raw DCB entry 0: 02000300 00000000

It is detecting hybrid graphics, which would be a combination (in your case) NVidia as the discreet chipset and either an Intel or lesser NVidia GPU as the embedded chipset.

Your graphics needs to be dealt with after the install. The installer scripts don't, because they are with non-free (licensed) drivers. 

Use "nomodeset" as the kernel boot option with the LiveCD and the installer should get through that... After that, on the fist boot after the install, you'll have to use nomodeset again to boot into the desktop... Then you'll have to install your nVidia driver...

Then you'll have to figure out how you want to deal with your hybrid graphics. Many choices. One is if your BIOS settings has an option to turn on/off the discrete chipset. Another is to turn on/off the discrete chipset using ACPI/vga_switheroo, which is what the next two options depend on, with a menu and scripts. Bumblebee presents a text menu and uses scripts to turn on/off. Ironhide is graphically base GUI that uses the same scripts as bumblebee (branched from Bumblebee) to turn on/off.

All the above just turns on/off the discreet card, which would save battery draw. The embedded card stays on all the time. When it turns on the discreet card (nVidia) it copies in the nvidia's xorg.conf file. When turned turn, it copies in a basic generic Xorg.conf.

Me, I figure turning on the discrete card having that cards drivers setop with it's Xorg.conf and leaving it on... is okay by me.  But that would b personal preference and how long you need that battery to last between recharge.

---

