---
title: "USB problem with 14.04"
date: 2014-08-06
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2014-08-06
When I remove the usb printer cable from the computer it crashes. 

The printer is not being recognised in lsusb.

I have connected the printer to another ubuntu machine and it works.

Is it possible to reinstall just the usb drivers (I do not refer to the printer drivers but the drivers that run the usb ports)?

---

### Post by ian-weisser on 2014-08-06
Do all USB ports have the same problem?

Try booting from an older kernel in GRUB. 'Drivers' (actually kernel modules) are specific to each kernel.
If the older kernel's USB works, then use it to reinstall the newer kernel.

If the older kernel has the same problem, then check your BIOS. Is it possible to boot from USB in BIOS? Was it possible?
If it's no longer possible, you may have a hardware issue, not an Ubuntu issue.
If it is possible, try booting a LiveUSB stick. Does it's USB drivers work proerly?

If the LiveUSB's drivers fail too, then reinstalling won't help. You have discovered a bug.
If the LiveUSB's drivers work fine, and you are able to print, then let us know so we can get into details.

---

