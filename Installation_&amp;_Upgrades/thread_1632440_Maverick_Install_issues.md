---
title: "Maverick Install issues"
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by smsaba on 2010-11-28
Hi
 I have an Toshiba SM30x-155 with Intel 1.6M processor, 1.5GB RAM and ATI radeon mobility 9600 (RV350) display card.
 Tried with Lucid and Maverick.

Lucid worked for sometime till Kernel update after that it broke.
Same with Maverick too.

However I have observed the following

Lucid / Maverick works fine with "FBDEV" driver with xorg.conf. But slow 2D and no 3D, no Compiz. 

Lucid / Maverick works fine with native xorg driver for ATI when installation kernel boot parameter (in the file /etc/default/grub) ACPI is set to off (ACPI=off). 2D is working fine, compiz working fine. But **no Battery indicator **or other ACPI features.


Is it possible to have a reasonable working settings to Lucid or Maverick?

Thanks
Saba

---

