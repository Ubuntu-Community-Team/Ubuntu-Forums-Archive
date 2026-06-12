---
title: "Ubuntu 12.04 won't load after update"
date: 2013-09-15
forum: Installation &amp; Upgrades
---

### Post by RaHorakhty on 2013-09-15
My recently updated Ubuntu displays the following errors when I try to boot.

Firmware and/or mailbox pointer not initialized or corrupted, signature = 0xsomebs cmd = PING_FW
ERROR: Firmware size mismatch (have 16382, expected 376836)
cx23345_initialize_codec() f/w load failed.

I tried the boot-repair utility w/out any luck!  I think it's the graphics driver.  Anyone know how to reverse the drivers to the generic-default?

---

### Post by maestrobwh1 on 2013-09-15
Try to boot with "xforcevesa"

When grub boot menu comes up, hit C then add that in front of "quiet splash" in the line starting with linux.  Then hit Ctrl+x

It will force the vesa driver: it will be at best 1024x768 but you can figure things out.

You could also try to boot with an older kernel.

---

### Post by RaHorakhty on 2013-09-21
@maesthrobwh1  That might have worked.  I actually ended up re-installing the entire OS, so they apparently released new drivers just a few days ago for my GPU/videocard.  I'll try booting w/ different paramaters next time it hits the fan.  Thanks! :P

---

