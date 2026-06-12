---
title: "Install query"
date: 2014-09-24
forum: Installation &amp; Upgrades
---

### Post by Milambar on 2014-09-24
For the past 6 months, my laptop has been running of a 32GB SDHC card, as the hard disk failed, and I couldn't afford to immediately replace it.

I have just ensconed a nice 250GB ssd in the laptop now. Is there any way to copy my current install from the SDHC card to the ssd, or do I need to download a new install dvd, and install from scratch?

---

### Post by ian-weisser on 2014-09-24
You can copy it.
You will need to use parted or similar partitioner to set up the new disk partition table.
You will need to install GRUB to the new disk.
You will need to check the new GRUB settings, that it will load from the correct device.
You will need to edit /etc/fstab to mount the proper disk after copying.

Be prepared to spend an afternoon discovering and troubleshooting issues.

---

