---
title: "DisplayLink and Ubuntu 13.10"
date: 2014-01-09
forum: Installation &amp; Upgrades
---

### Post by shaunconn on 2014-01-09
Hi

I have a Lenovo LT1421 USB external monitor, which ubuntu recognises, so in lsusb I have:
Bus 003 Device 015: ID 17e9:03e0 DisplayLink

and in dmesg:
[ 2462.124838] usb 3-4: new high-speed USB device number 15 using xhci_hcd
[ 2462.144951] usb 3-4: New USB device found, idVendor=17e9, idProduct=03e0
[ 2462.144960] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2462.144965] usb 3-4: Product: Lenovo LT1421 wide
[ 2462.144968] usb 3-4: Manufacturer: DisplayLink
[ 2462.144971] usb 3-4: SerialNumber: 6V9CAAB7
[ 2462.146656] [drm] vendor descriptor length:17 data:17 5f 01 00 15 05 00 01 03 00 04
[ 2462.226249] udl 3-4:1.0: fb1: udldrmfb frame buffer device
[ 2462.226258] [drm] Initialized udl 0.0.1 20120220 on minor 1

I do not see the display in xrandr (or in the displays panel).  I have edited /etc/modprobe.d/blacklist-framebuffer.conf to contain these two lines at the end:
# blacklist udl
blacklist udlfb

I have tried following the awful instructions on displaylink.org but there are lots of broken links and lots of software with missing dependencies and the like, and very little success stories.  I have read the posts in this forum and others, but none of the solutions seem to be aimed at recent kernels (mine is 3.11 which is supposed to have DisplayLink drivers built in).   

Has anyone got this working in ubuntu 13.x, and if so, can you help me please?

Thanks

Shaun

---

