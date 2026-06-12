---
title: "Installation with fake raid and lvm on 8.04 results in Device lookup failure"
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by praenti on 2008-10-01
Hi,

having some problems with an installation I made on my computer. Tried to install my Ubuntu with Fakeraid-Support (Intel ICH9 on a Asus P5E) on a RAID1. Using dmraid from the Live-CD works great, but when I install it like the described in the FakeRaidHowto, I'm getting always "Device lookup failure" when I tried to "dmraid -ay". But dmraid -r shows me the raid.

Also tried the option ignore_hpa=0 (on libata module, did that over /etc/modprobe.d/libata-options) because my first installation broke my raid.

The strange thing is, that I can see my logical volumes from LVM including the root-fs under /dev/mapper. But I cannot mount my /boot because of this issue.

Anyone has an idea, what breaks teh dmraid support?

Cheers,
Michael

---

