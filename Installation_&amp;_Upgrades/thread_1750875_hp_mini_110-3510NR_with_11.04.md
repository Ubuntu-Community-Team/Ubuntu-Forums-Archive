---
title: "hp mini 110-3510NR with 11.04"
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by dolphs on 2011-05-06
Hi I tried to install both ubuntu and lubuntu 11.04 on my [HP mini 110-3510NR]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02664908&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN"), but the install freezes so I cannot install. When I either run the live session of ubuntu from usb stick or when I execute the installer to hard disk it locks/freezes at:

...
Starting configure network device security
Starting configure network device


USB Stick created with Universal-USB-Installer-1.8.4.6.


Win7 runs (un)fortunately with the WLAN driver. Please let me know how to install to hard disk

---

### Post by dolphs on 2011-05-06
in an effort disabling the wlan while booting I apparently succeeded and indeed Ubuntu got installed OK. After that I applied updates and broadcom proprietary driver in Ubuntu. Now the HP Mini boots! However it seems no 5GHZ available :/

---

### Post by HelpdeskSean on 2011-07-25
Confirmed.  I was having a similar issue where my Ubuntu 11.04 USB device would boot to the splash screen and hang.  I disabled my WLAN/Bluetooth device in the BIOS and it worked perfectly the next time.  Processed updates after install, and re-enabled device. This is with an HP MINI 5103.

---

