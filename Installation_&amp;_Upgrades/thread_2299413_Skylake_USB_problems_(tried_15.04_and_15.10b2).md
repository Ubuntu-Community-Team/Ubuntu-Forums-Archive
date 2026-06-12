---
title: "Skylake USB problems (tried 15.04 and 15.10b2)"
date: 2015-10-18
forum: Installation &amp; Upgrades
---

### Post by fayl1861 on 2015-10-18
So I've recently upgraded my rig to the new skylake architecture, but I'm having a horrible time getting the live USB to boot.

Basically, it seems to be having some sort of problem with the USB controller(s). The following errors happen before dropping to a busybox terminal:
[http://i.imgur.com/A5NBonK.jpg]("http://i.imgur.com/A5NBonK.jpg")

I've looked around, read various things. Some say those errors have to do with some EFI bios' "Fast Boot" option, but disabling or enabling that seems to make no difference. I've also tried the "i915.preliminary_hw_support=1" flag (to fix intel graphics) but again, it still falls to a busybox terminal with the same errors.

I'm probably missing something obvious but after hours of toiling I've made little progress. Any insight is greatly appreciated.


Hardware specifics:
ASUS Z170-deluxe motherboard with the following hardware:
- ASMEDIA usb 3.1 controller + intel 100 series USB (Tried both)
- ASMEDIA 106x sata3 controller + intel 100 series sata3 controller (tried both)

---

