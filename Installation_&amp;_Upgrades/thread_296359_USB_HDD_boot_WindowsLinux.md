---
title: "USB HDD boot? Windows/Linux"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by rebelfallen on 2006-11-09
I have a 250GB maxtor HDD external usb that I want to be able to:
1) Boot with from home. I use grub and run Fedora and Ubuntu
2) Boot from work. I run Windows XP Professional

To me it only seems logical and easy to do, there should just be some setting I can set that allows me to boot. However somewhere along the line it gets super complicated and I don't even know where to start. Does anyone have any ideas?

Thank you.

---

### Post by kidders on 2006-11-09
Hi there,

Assuming of course that your both BIOSes support booting from USB devices, the simplest thing to do is reorder your boot priority, so that USB drives are checked first.

---

### Post by rebelfallen on 2006-11-09
My bios on my windows machine does not. Do you know how I could enable that?

---

### Post by kidders on 2006-11-09
Short of a BIOS firmware update that includes the feature, you can't afaik. Check with your manufacturer.

---

