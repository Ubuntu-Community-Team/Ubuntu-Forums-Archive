---
title: "Boot Ubuntu from USB port"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by gaparri on 2007-10-29
I was able to install and boot Ubuntu in the usb port from a laptop (2.5 in) drive but all attempts to do the same with an old 3.5 in desktop drive have failed.

     I can't install Ubuntu into the usb port and unlike the laptop hd I have all these strap options.  I tried every strap position on the hdd.  So I installed the HDD internally and installed Ubuntu but when I tried to boot from USB I got a grub error 25 code.

Any suggestions?

---

### Post by traderpats on 2007-10-30
I tracked my boot issue down to a bios setting.  The external usb hdd wasn't being found at boot.  I enabled legacy support in bios, rebooted and all was good.  I already had usb1&usb2 support enabled so I don't know why this was an issue.  I may have also changed "Reset Configuration Data" from disabled to enabled but not sure.  Anyway hope this helps.

---

