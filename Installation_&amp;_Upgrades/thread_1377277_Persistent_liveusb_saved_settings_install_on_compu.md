---
title: "Persistent liveusb saved settings install on computer?"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by antel on 2010-01-10
do the settings, saved on my persistent liveusb such as color schemes and applications, move to the computer when i use the usb to install ubuntu?

---

### Post by efflandt on 2010-01-10
No, it always does a normal installation based on the iso you used to create the bootable live/install iso.  If you set up a normal user when running persistent, after you install and boot your new system, you can connect your USB device which should automount, create a directory for a mount point (for example **sudo mkdir /media/vdisk**), then loop mount casper-rw to copy anything from your persistent home dir (**sudo mount -o loop /whatever_your_usb_is/casper-rw /media/vdisk**).

---

