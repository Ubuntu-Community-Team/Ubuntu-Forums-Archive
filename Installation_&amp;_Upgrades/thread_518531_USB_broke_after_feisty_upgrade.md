---
title: "USB broke after feisty upgrade"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by gro.utnubu on 2007-08-06
Hi there, I just upgraded to Feisty.  THis is an old old laptop, and both of my USB inputs are janky, but, before the upgrade, one of them still worked.  Two different USB devices light up, but neither gets detected.  dmesg says error -71 (see below)

At present lsusb says
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

 lsmod | grep usb
usbcore               131480  3 ehci_hcd,uhci_hcd

 lspci | grep -i usb
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)


 dmesg
[ 1116.248000] usb 2-1: new low speed USB device using uhci_hcd and address 14
[ 1116.372000] usb 2-1: device descriptor read/64, error -71
[ 1116.600000] usb 2-1: device descriptor read/64, error -71
[ 1116.816000] usb 2-1: new low speed USB device using uhci_hcd and address 15
[ 1116.936000] usb 2-1: device descriptor read/64, error -71
[ 1117.160000] usb 2-1: device descriptor read/64, error -71
[ 1117.376000] usb 2-1: new low speed USB device using uhci_hcd and address 16
[ 1117.784000] usb 2-1: device not accepting address 16, error -71
[ 1117.896000] usb 2-1: new low speed USB device using uhci_hcd and address 17
[ 1118.304000] usb 2-1: device not accepting address 17, error -71
[ 1215.300000] usb 2-1: new low speed USB device using uhci_hcd and address 18
[ 1215.424000] usb 2-1: device descriptor read/64, error -71
[ 1215.652000] usb 2-1: device descriptor read/64, error -71
[ 1215.868000] usb 2-1: new low speed USB device using uhci_hcd and address 19
[ 1215.988000] usb 2-1: device descriptor read/64, error -71
[ 1216.212000] usb 2-1: device descriptor read/64, error -71
[ 1216.428000] usb 2-1: new low speed USB device using uhci_hcd and address 20
[ 1216.836000] usb 2-1: device not accepting address 20, error -71
[ 1216.948000] usb 2-1: new low speed USB device using uhci_hcd and address 21
[ 1217.356000] usb 2-1: device not accepting address 21, error -71
[ 1217.636000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[ 1218.268000] usb 1-1: device descriptor read/64, error -71
[ 1219.024000] usb 1-1: device descriptor read/64, error -71
[ 1219.276000] usb 1-1: new low speed USB device using uhci_hcd and address 3
[ 1220.032000] usb 1-1: device descriptor read/64, error -71
[ 1220.788000] usb 1-1: device descriptor read/64, error -71
[ 1221.040000] usb 1-1: new low speed USB device using uhci_hcd and address 4
[ 1221.636000] usb 1-1: device not accepting address 4, error -71
[ 1221.796000] usb 1-1: new low speed USB device using uhci_hcd and address 5
[ 1222.392000] usb 1-1: device not accepting address 5, error -71


and uname -a
Linux xxxxox 2.6.20-16-386 #2 Thu Jun 7 20:16:13 UTC 2007 i686 GNU/Linux


Thanks for your help
-seth

---

### Post by JudasReanimated on 2007-08-06
They most likely require proprietary drivers, which Fiesty has left out. You may be able to use NDISwrapper to use windows drivers and fic the issue.

---

### Post by intel on 2007-08-12
try changing/switching the USB ports, try it sometimes that solves that exact error.

---

