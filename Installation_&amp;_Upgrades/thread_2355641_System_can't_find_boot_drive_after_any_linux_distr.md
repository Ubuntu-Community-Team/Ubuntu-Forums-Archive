---
title: "System can't find boot drive after any linux distro installation."
date: 2017-03-14
forum: Installation &amp; Upgrades
---

### Post by wyso on 2017-03-14
The distro installation, whether it's ubuntu, mint, lubuntu, or opensuse, always seems to go through okay, then upon rebooting, I switch my boot drive from my usb to the hard drive in the bios settings. And when it reboots I consistantly get an error message saying "No bootable device found". When I look at all other forums, people seem to mention secure boot being an issue, but my bios doesn't have this setting. Thanks for the help in advance.

edit: using acer desktop previously with windows 7 x64 installed, using latest version installation for each distro.

---

### Post by Bucky Ball on 2017-03-15
Welcome. Remove the USB completely at the end of the install (which I think you are instructed to do when requested to reboot after install). 

Best if you run the bootinfo script and post the link that spits out at the end here so we can have a look at the configuration of your drive currently and see what's where. :)

See the link in my signature at the bottom of this script (first line, last red link). You can use Boot Repair from a live session and choose to run bootinfo, not the 'Recommended Repair' (although that may fix the issues, best to have a look first as it may not and may spit superfluous grubs on to partitions).

---

