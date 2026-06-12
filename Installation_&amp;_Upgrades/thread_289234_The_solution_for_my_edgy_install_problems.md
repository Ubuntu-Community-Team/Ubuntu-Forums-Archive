---
title: "The solution for my edgy install problems"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by itchanddino on 2006-10-30
Upon booting the livecd and regularly running the installer, the boot would just hang.  I fooled around with different settings for the boot and ended up finding the following:
When the livecd loads, hit F6 to edit the boot orders. Then, add acpi=off to the end and hit enter.
After this, the installer proceeded as normal.  Hope this helps!

Edit: Alternatively, you can just disable ACPI in the bios, that seems to work better.

---

