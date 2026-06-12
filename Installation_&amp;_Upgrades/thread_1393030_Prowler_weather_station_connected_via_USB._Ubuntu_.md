---
title: "Prowler weather station connected via USB. Ubuntu 9.10 doesn't recognise it"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by jvan_ca on 2010-01-28
I have a Prowler weather station connected via USB.  Ubuntu does not recognize this.
I would assume that the problem lies within 1941:8021 Dream Link USB Missile Launcher.
 Could you please assist.
 Thank you in advance for any advice that you might have.
 Joel
 Terminal readout is:
user@user-laptop:~$ lsusb
Bus 005 Device 002: ID 1941:8021 Dream Link USB Missile Launcher
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ca:1837 Ricoh Co., Ltd Visual Communication Camera VGP-VCC4 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
user@user-laptop:~$ mount | grep ^/dev
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
joel@joel-laptop:~$ dmesg|tail -40
[ 16.859344] iwlagn 0000:06:00.0: loaded firmware version 228.61.2.24
[ 17.074072] Registered led device: iwl-phy0::radio
[ 17.074093] Registered led device: iwl-phy0::assoc
[ 17.074113] Registered led device: iwl-phy0::RX
[ 17.074131] Registered led device: iwl-phy0::TX
[ 17.101154] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[ 17.103261] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[ 17.104167] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[ 17.104906] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[ 17.105837] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[ 17.127813] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 17.205177] usbcore: deregistering interface driver uvcvideo
[ 17.273992] Linux video capture interface: v2.00
[ 17.276604] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:1837)
[ 17.279214] input: UVC Camera (05ca:1837) as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input11
[ 17.279258] usbcore: registered new interface driver uvcvideo
[ 17.279261] USB Video Class driver (v0.1.0)
[ 17.312044] usbcore: deregistering interface driver uvcvideo
[ 17.380712] Linux video capture interface: v2.00
[ 17.383355] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:1837)
[ 17.384064] input: UVC Camera (05ca:1837) as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input12
[ 17.384109] usbcore: registered new interface driver uvcvideo
[ 17.384113] USB Video Class driver (v0.1.0)
[ 19.330603] usbcam: registering driver r5u870 0.11.3
[ 19.330635] usbcore: registered new interface driver r5u870
[ 19.458233] ppdev: user-space parallel port driver
[ 42.351517] wlan0: authenticate with AP 00:14:6c:4e:72:72
[ 42.353264] wlan0: authenticated
[ 42.353267] wlan0: associate with AP 00:14:6c:4e:72:72
[ 42.356081] wlan0: RX AssocResp from 00:14:6c:4e:72:72 (capab=0x431 status=0 aid=2)
[ 42.356083] wlan0: associated
[ 42.378038] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 53.068699] wlan0: no IPv6 routers present
[ 436.000777] CE: hpet increasing min_delta_ns to 15000 nsec
[ 483.913077] usb 5-1: new low speed USB device using uhci_hcd and address 2
[ 484.101151] usb 5-1: configuration #1 chosen from 1 choice
[ 484.173837] usbcore: registered new interface driver hiddev
[ 484.212067] generic-usb 0003:1941:8021.0001: hiddev96,hidraw0: USB HID v1.00 Device [HID 1941:8021] on usb-0000:00:1d.0-1/input0
[ 484.212105] usbcore: registered new interface driver usbhid
[ 484.212111] usbhid: v2.6:USB HID core driver
user@user-laptop:~$

---

### Post by Ambricka on 2010-01-31
it's using a generic usb chip.
I had some success using this program [http://www.pendec.dk/weatherstation.htm](http://www.pendec.dk/weatherstation.htm)
However there are a couple of bugs that I'm trying to fix right now.

---

### Post by chrisp_duck on 2010-06-20
I have a similar problem...  My device is the one featured here ([http://www.maplin.co.uk/module.aspx?moduleno=223254](http://www.maplin.co.uk/module.aspx?moduleno=223254)) "USB Wireless Weather Forecaster".  It's got "Weather Station - Model: WH1081" on the back...

Prior to installation, I ran "update-usbids" to make sure I have the  latest available info.

The following is seen in /var/log/messages upon USB device insertion: -
kernel: [634601.160205] usb 1-4.2.2: new low speed USB device using ehci_hcd and address 8
kernel: [634601.277991] usb 1-4.2.2: configuration #1 chosen from 1 choice
kernel: [634601.285731] generic-usb 0003:1941:8021.0006: hiddev97,hidraw4: USB HID v1.00 Device [HID 1941:8021] on usb-0000:00:1a.7-4.2.2/input0

# lsusb | grep 1941           
Bus 001 Device 008: ID 1941:8021 **Dream Link USB Missile Launcher**

The provided software "EasyWeather" ([http://proweatherstation.com/easyweather/easyweather.htm](http://proweatherstation.com/easyweather/easyweather.htm)) and the oft-recommended software "Cumulus" ([http://sandaysoft.com/products/cumulus](http://sandaysoft.com/products/cumulus)) both seem to work perfectly within "wine" on my Ubuntu 10.4 Linux and it seems a shame that I can not link the software to the USB device...

Any help or advice would be greatly appreciated!

---

