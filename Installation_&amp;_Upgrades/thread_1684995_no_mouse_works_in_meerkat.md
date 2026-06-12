---
title: "no mouse works in meerkat"
date: 2011-02-10
forum: Installation &amp; Upgrades
---

### Post by willieray25 on 2011-02-10
Fresh install AMD64 10.10 alternative (for RAID).  No mouse will work.  I have tried 3.  My old optical M$ PS2 / USB mouse that I have had for years, that worked fine on Lucid yesterday before wipeout and clean install.  dell cheapo usb wheel mouse and apple pro mouse usb.  all light up like they want to work.  LSUSB shows them.  Dmesg shows them when I unplug and replug.  The mouse cursor is there but will not move.  Any ideas team?

Thanks!

willieray

---

### Post by dino99 on 2011-02-10
sudo update-usbids && sudo update-pciids

and watch the logs

---

### Post by willieray25 on 2011-02-10
ran the commands.  No change.  No mouse will work.

---

