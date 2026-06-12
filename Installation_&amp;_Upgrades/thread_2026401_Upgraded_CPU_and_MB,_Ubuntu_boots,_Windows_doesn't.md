---
title: "Upgraded CPU and MB, Ubuntu boots, Windows doesn't"
date: 2012-07-15
forum: Installation &amp; Upgrades
---

### Post by CaptConan on 2012-07-15
Hello, I have a dual-boot 10.04/XPSP3 that's been working fine and I finally got around to upgrading the core hardware of my computer, including replacing the motherboard and CPU. I'm aware that this might cause driver issues and was ready to reinstall the OSs if necessary. However after swapping the hardware, and selecting 10.04 from the grub loader, Ubuntu launched into the GUI just fine (and faster than ever). However when I try to launch XP, it just begins to load, and then the PC resets and starts back at the BIOS. It does the same for safe mode.

When I booted off the XP3 installation CD, and after all the drivers were loaded, setup claimed it could not find any hard disks to install Windows. Any thoughts?

---

### Post by sudodus on 2012-07-15
I can only guess: maybe it is a copy protection feature, if you have an OEM installation and disk for Windows. I'm thinking that the installed system does not recognize the computer it was installed to, and the installation CD disk does not recognize the vendor's OEM signature.

If you have a general installation disk for Windows, it should recognize 'any' computer and its hard disk drives. So in that case I'd be puzzled.

---

### Post by Shadius on 2012-07-15
> **sudodus said:**
> I can only guess: maybe it is a copy protection feature, if you have an OEM installation and disk for Windows. I'm thinking that the installed system does not recognize the computer it was installed to, and the installation CD disk does not recognize the vendor's OEM signature.

If you have a general installation disk for Windows, it should recognize 'any' computer and its hard disk drives. So in that case I'd be puzzled.

I think this is the reason because when I cloned my Windows XP, I thought it would work on my other computer, but it didn't. It has to do something with the OEM.

---

### Post by Cheesemill on 2012-07-15
> When I booted off the XP3 installation CD, and after all the drivers  were loaded, setup claimed it could not find any hard disks to install  Windows. Any thoughts?I think that you need the XP SATA drivers for your motherboard.

As XP pre-dates SATA it doesn't have the necessary drivers needed to detect drives on newer motherboards.
You can either copy the drivers onto a floppy and use that during the XP installation or slipstream the drivers into your XP CD.

---

### Post by darkod on 2012-07-15
Also double check whether the sata mode in BIOS is set to AHCI or IDE. AHCI is better and faster, but WinXP needs IDE unless you had the AHCI drivers loaded and they match.
In IDE it might boot without adding any drivers, if you're lucky. I think your old setting was IDE (depending how old was the old board, AHCI options might not have existed).

Even win7 is tricky about this. If you install it with IDE option and later switch to AHCI in bios, it will give you the blue screen. Ubuntu on the other hand keeps working even after such switch.

EDIT PS: I am talking about making your old installation work, not about a new install. Changing to IDE should work I think.

Otherwise, for a new install you would need the drivers on a floppy (strictly floppy) or slipstreamed into the CD. Or again, using IDE might work without additional drivers.

---

