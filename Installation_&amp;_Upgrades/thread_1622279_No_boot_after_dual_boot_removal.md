---
title: "No boot after dual boot removal"
date: 2010-11-15
forum: Installation &amp; Upgrades
---

### Post by wphred on 2010-11-15
I removed windows vista from my machine via Gparted. Then used the command sudo update-grub. I noticed the portion of the hard drive that had windows was now unallocated. I rebooted my machine to see what impact that would have and got the following:

Intel UNDI, PXE-2.1 (build 082)
Copyright (C) 1997-2000 Intel Corporation

For Realtek RTL8101E/8102E PCI-E Ethernet Controller v1.05 (071227)

CLIENT MAC ADDRF: 00 26 6C 33 96 CE  GUID: FCBA3670-D104-11DE-BBA9-00266c3396ce
PXE-E53: No boot filename received

PEX-MOF: Exiting PXE ROM.

Blinking cursor

Can anyone help me out? It seems that during the boot process my computer cannot find the ethernet controller, or is this an indication that something else is wrong?

---

### Post by Arand on 2010-11-15
PXE is network booting, which if you are not using it, is probably irrelevant (you could disable it trying PXE booting in the bios, just to save some boot time...)

How did you have the boot setup before you removed windows? Did you install a dual-boot with a grub menu at the start?

For reinstalling grub, you likely would've wanted to use grub-install instead of -update.

To reinstall it from a liveCD, follow the steps here:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
...which should hopefully get everything working again.

- arand

---

### Post by sikander3786 on 2010-11-15
**Arand** is right. Seems like Bios was unable to find anything bootable in the MBR of your HDD so it bypassed it and went for a PXE boot.

I would rather prefer to look in the Bios if somehow my first boot device didn't changed from HDD to LAN.

You can reinstall Grub following the link in the above post.

If you want to, you can post the output of bootinfoscipt as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It will help us better understand your current situation and thus advise accordingly. You'll need to run that script from a Live CD.

Please wrap the output using proper code tags # from post menu.

---

### Post by wphred on 2010-11-19
Thank you both. I'm back up and running.

---

