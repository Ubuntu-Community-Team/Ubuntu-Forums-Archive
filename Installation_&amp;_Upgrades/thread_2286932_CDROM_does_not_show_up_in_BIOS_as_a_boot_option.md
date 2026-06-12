---
title: "CDROM does not show up in BIOS as a boot option"
date: 2015-07-15
forum: Installation &amp; Upgrades
---

### Post by jim-anderson on 2015-07-15
I have an ASUS X551M laptop. I was running a multiboot environment with Windows Vista, Crunchbang Linux (Waldorf) and Lubuntu 14.04.01. The system crashed and I was not able to boot, so I have been trying to reinstall. Crunchbang is more or less in maintenance mode, so I am planning to move to Ubuntu, probably kubuntu, and lubuntu on my different PC's and most likely will install kubuntu on this ASUS laptop.

Because I could not load up any operating systems, I decided to start over and I reset the BIOS to the default options. I have since turned off the secure boot option and enabled the CSM mode.

When I bring up the BIOS now, I do not see the CDROM drive as a boot option in the BIOS. In was available before I reset the default options of the BIOS. If I look at the 'Advance' tab in the BIOS, I can look at the 'SATA Configuration' and see that SATA Port1 is an ATAPI CDROM, model TSSTcorp CDDVDW SN-208F.

Can anyone tell me if there is something I have to do in the BIOS to allow the CDROM to become a boot option. When I look at the 'Boot' tab in the bios, I see there is an "Add New Boot Option". If I select that option, there are several choices available, but I have not idea how to create an option that makes the CDROM available.

Jim A.

---

### Post by jim-anderson on 2015-07-15
I am not sure what happened, but I was playing with the laptop trying different things. I tried rebooting and hitting the escape key and the F2 key. To my surprise, a menu popped up asking where to boot from and one option was the CDROM. I selected it and I was able to boot from the CDROM. Even better, next time I went into the BIOS, the CDROM now appears as a boot option that I can select. I'm not sure why this happened, but this issue is resolved.

---

