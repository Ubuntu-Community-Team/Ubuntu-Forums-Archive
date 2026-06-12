---
title: "Ubuntu Server 14.04 install to MSI Cubi display not working"
date: 2016-03-03
forum: Installation &amp; Upgrades
---

### Post by hansmc2 on 2016-03-03
I just did a clean install of Ubuntu Server 14.04 on to a MSI Cubi and display is not working. The first time I booted it up it went part way through the boot process and then the screen went black and would not come back. I tried booting it a few more times. It sounds like it is booting but just not showing anything. I then booted into recovery mode from GRUB and then chose normal boot. From their it booted up fine and I was able to log in. Any ideas how to get the display to work right on a normal boot? Thanks

---

### Post by hansmc2 on 2016-03-05
After trying a bunch of different things, it seems to be working if I set the kernel boot parameter acpi=off from the grub menu. Why is that? What functionality will I be missing if I make that permanent? Is there any way I can figure out what part of acpi my computer is not compatible with? Thanks

---

### Post by hansmc2 on 2016-03-26
I was using a mini display port to VGA adapter. It seems Ubuntu does not support that. Once I switched to a HDMI cable it seems to have solved my display problem.

---

