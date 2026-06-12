---
title: "No keyboard or mouse on login screen after lucid upgrade"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by skinnny on 2010-12-19
Hi

I have an intel mac mini, dual-booting OSX and ubuntu via rEFIt.
I just upgraded 8.04 LTS to 10.04 LTS via update-manager.
All seemed to go without a hitch until the restart.
I ended up on the 10.04 login screen with unresponsive usb mouse and keyboard.
I was able to ssh into the mac from another pc and get some info.

'lsusb' output:
Bus 005 Device 004: ID 05ac:8205 Apple, Inc. Bluetooth HCI
Bus 005 Device 003: ID 05ac:8240 Apple, Inc. IR Receiver [build-in]
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 413c:2001 Dell Computer Corp. Keyboard HID Support
Bus 002 Device 002: ID 413c:1001 Dell Computer Corp. Keyboard Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

'dmesg|tail' output after unplugging the mouse:
[   20.972239] type=1505 audit(1292777457.021:9):  operation="profile_load" pid=932 name="/usr/lib/firefox-3.6.13/firefox-*bin"
[   20.976046] type=1505 audit(1292777457.025:10):  operation="profile_load" pid=932 name="/usr/lib/firefox-3.6.13/firefox-*bin//firefox_java"
[   20.978260] type=1505 audit(1292777457.025:11):  operation="profile_load" pid=932 name="/usr/lib/firefox-3.6.13/firefox-*bin//firefox_openjdk"
[   21.169336] apm: BIOS not found.
[   21.612089] ppdev: user-space parallel port driver
[   22.344301] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   22.344493] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   33.076055] eth0: no IPv6 routers present
[  112.712360] cfg80211: Found new beacon on frequency: 5220 MHz (Ch 44) on phy0
[ 1037.304114] usb 3-1: USB disconnect, address 2

'dmesg|tail' output after plugging the mouse back in:
[   21.169336] apm: BIOS not found.
[   21.612089] ppdev: user-space parallel port driver
[   22.344301] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   22.344493] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   33.076055] eth0: no IPv6 routers present
[  112.712360] cfg80211: Found new beacon on frequency: 5220 MHz (Ch 44) on phy0
[ 1037.304114] usb 3-1: USB disconnect, address 2
[ 1074.916056] usb 3-1: new low speed USB device using uhci_hcd and address 3
[ 1075.092265] usb 3-1: configuration #1 chosen from 1 choice
[ 1075.112801] hid: Unknown parameter `pb_fnmode'

End of 'dmesg' output after plugging a usb flash drive in:
[  112.712360] cfg80211: Found new beacon on frequency: 5220 MHz (Ch 44) on phy0
[ 1037.304114] usb 3-1: USB disconnect, address 2
[ 1074.916056] usb 3-1: new low speed USB device using uhci_hcd and address 3
[ 1075.092265] usb 3-1: configuration #1 chosen from 1 choice
[ 1075.112801] hid: Unknown parameter `pb_fnmode'
[ 1103.520098] usb 3-1: USB disconnect, address 3
[ 1118.452075] usb 3-1: new full speed USB device using uhci_hcd and address 4
[ 1118.632052] usb 3-1: device descriptor read/64, error -71
[ 1118.856051] usb 3-1: device descriptor read/64, error -71
[ 1119.072054] usb 3-1: new full speed USB device using uhci_hcd and address 5
[ 1119.192052] usb 3-1: device descriptor read/64, error -71
[ 1119.416051] usb 3-1: device descriptor read/64, error -71
[ 1119.632052] usb 3-1: new full speed USB device using uhci_hcd and address 6
[ 1119.666135] usb 3-1: not running at top speed; connect to a high speed hub
[ 1119.700297] usb 3-1: configuration #1 chosen from 1 choice
[ 1119.762243] Initializing USB Mass Storage driver...
[ 1119.762452] scsi4 : SCSI emulation for USB Mass Storage devices
[ 1119.762903] usbcore: registered new interface driver usb-storage
[ 1119.762909] USB Mass Storage support registered.
[ 1119.766212] usb-storage: device found at 6
[ 1119.766217] usb-storage: waiting for device to settle before scanning
[ 1124.765401] usb-storage: device scan complete
[ 1124.768368] scsi 4:0:0:0: Direct-Access     Sony     Storage Media    0100 PQ: 0 ANSI: 0 CCS
[ 1124.771350] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 1124.785331] sd 4:0:0:0: [sdb] 7927808 512-byte logical blocks: (4.05 GB/3.78 GiB)
[ 1124.788324] sd 4:0:0:0: [sdb] Write Protect is off
[ 1124.788330] sd 4:0:0:0: [sdb] Mode Sense: 43 00 00 00
[ 1124.788335] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1124.803324] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1124.803332]  sdb: sdb1
[ 1124.894329] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1124.894337] sd 4:0:0:0: [sdb] Attached SCSI removable disk

The drive did not mount and was not present in the output of 'df'.
Anyone able to help me fix this?
I really don't want to have to do a clean install and setup my system all over again.
Also I installed x11vnc via ssh so I can now also login to the desktop environment... if that somehow helps to fix this!

Thanks.

Colin

---

### Post by ajgreeny on 2010-12-19
On the assumption that a mac BIOS is similar to a windows style PC, check to see if legacy USB is enabled.

I needed that for my USB keyboard to work in the grub menu, so it may help you.

---

### Post by skinnny on 2010-12-19
> **ajgreeny said:**
> On the assumption that a mac BIOS is similar to a windows style PC, check to see if legacy USB is enabled.  I needed that for my USB keyboard.

Thanks but I've already been down that road... turns out the mac doesn't have a BIOS!  Got something called EFI instead, which I'm currently looking into to see if it has similar USB settings.  Not found anything so far tho.

---

### Post by skinnny on 2010-12-21
bump after being moved to this category

---

