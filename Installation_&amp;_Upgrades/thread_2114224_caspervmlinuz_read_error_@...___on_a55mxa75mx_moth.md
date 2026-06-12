---
title: "casper/vmlinuz: read error @...   on a55mx/a75mx motherboard"
date: 2013-02-09
forum: Installation &amp; Upgrades
---

### Post by mrabc1234 on 2013-02-09
tried to install ubuntu-12.10-desktop-i386.iso (hash ok) on a55mx/a75mx motherboard 3 times from same usb harddrive (drive is new, should be fine). 

same error all the time: "/casper/vmlinuz:read error @xxx" where xxx are shifting numbers, e.g. 5172760.

suggestions sincerely appreciated. thanks.

---

### Post by tgalati4 on 2013-02-09
Try a different cable.  Unpacking the compressed linux image and reading it at the same time could cause timing and read issues.  Perhaps your USB cable is not rated for the speed of the drive?  Try different USB ports.

I would use unetbootin and create the iso on a usb flash drive.  Since they have slower controllers, they might work better with your USB port.

---

