---
title: "Ubuntu 10.04 external USB 320 GB HDD installation problem"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by mrnewba on 2010-05-15
Hello, I am trying to install my Samsung S2 Portable 320Gb external USB HDD but I doesn't seems to be detected by the OS.

Here is the output of dmesg:
```
[ 2999.693498] generic-usb 0003:1C4F:0003.000D: input,hidraw0: USB HID v1.10 Mouse [SIGMACH1P U+P Mouse] on usb-0000:00:0b.0-2/input0
[ 3015.412596] usb 1-6: new high speed USB device using ehci_hcd and address 17
[ 3015.546417] usb 1-6: configuration #1 chosen from 1 choice
[ 3048.603914] usb 1-6: USB disconnect, address 17
[ 3055.132110] usb 1-6: new high speed USB device using ehci_hcd and address 18
[ 3055.266553] usb 1-6: configuration #1 chosen from 1 choice
[ 3127.043625] usb 1-6: USB disconnect, address 18
[ 3141.932070] usb 1-6: new high speed USB device using ehci_hcd and address 19
[ 3142.065285] usb 1-6: configuration #1 chosen from 1 choice
[ 3332.784913] usb 1-6: USB disconnect, address 19
[ 3368.552120] usb 1-6: new high speed USB device using ehci_hcd and address 20
[ 3368.688379] usb 1-6: configuration #1 chosen from 1 choice
[ 4021.012712] usb 1-6: USB disconnect, address 20
[ 4106.504102] usb 1-6: new high speed USB device using ehci_hcd and address 21
[ 4106.638583] usb 1-6: configuration #1 chosen from 1 choice

```Thanks!

---

### Post by dino99 on 2010-05-15
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

install usbmount and mountmanager (set your prefs)

---

### Post by efflandt on 2010-05-15
What you posted from dmesg looks incomplete, unless it is stumbling trying to get it to power up.  Is that the result of **dmesg | grep usb**, or something else? What is the output of **lsusb** while it is connected?

Does it work on any other computer or OS?  Does the drive light up when you plug it into USB.  Are you sure that the USB plug is not upside down?

Normally dmesg would show something like this when it finds a usb drive:

```
[    0.917687] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.068837] usb 1-1: configuration #1 chosen from 1 choice
[    1.088658] usbcore: registered new interface driver usb-storage
[    1.089000] usb-storage: device found at 2
[    1.089002] usb-storage: waiting for device to settle before scanning
[    1.089102] usbcore: registered new interface driver hiddev
[    1.089964] input: Western Digital  External HDD     as /devices/pci0000:00/0000:00:02.2/usb1/1-1/1-1:1.1/input/input4
[    1.090109] generic-usb 0003:1058:0705.0001: input,hidraw0: USB HID v1.10 Device [Western Digital  External HDD    ] on usb-0000:00:02.2-1/input1
```

---

### Post by mrnewba on 2010-05-16
> **efflandt said:**
> What you posted from dmesg looks incomplete, unless it is stumbling trying to get it to power up.  Is that the result of **dmesg | grep usb**, or something else? What is the output of **lsusb** while it is connected?

Does it work on any other computer or OS?  Does the drive light up when you plug it into USB.  Are you sure that the USB plug is not upside down?

Normally dmesg would show something like this when it finds a usb drive:

```
[    0.917687] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.068837] usb 1-1: configuration #1 chosen from 1 choice
[    1.088658] usbcore: registered new interface driver usb-storage
[    1.089000] usb-storage: device found at 2
[    1.089002] usb-storage: waiting for device to settle before scanning
[    1.089102] usbcore: registered new interface driver hiddev
[    1.089964] input: Western Digital  External HDD     as /devices/pci0000:00/0000:00:02.2/usb1/1-1/1-1:1.1/input/input4
[    1.090109] generic-usb 0003:1058:0705.0001: input,hidraw0: USB HID v1.10 Device [Western Digital  External HDD    ] on usb-0000:00:02.2-1/input1
```

Those were the last lines of dmesg... I didn't grep'ed anything. :( The drive light up when I plug it into USB. Everything works fine on those USB ports, mouse, webcam, pendrive. And this HD works fine on another ubuntu 10 box. It seems the problem is with this laptop, wich is a hp dv6120br. I had problems putting the wifi adapter to work. But as I said, every other USB device I have works fine. That's weird.

This laptop has windows installed, and the drive works ok on it. omg. :(

dmesg:
```
(a lot of lines)
[ 2178.776459] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[ 2179.248376] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2189.824075] wlan0: no IPv6 routers present
[ 2374.496108] usb 1-6: new high speed USB device using ehci_hcd and address 3
[ 2374.630349] usb 1-6: configuration #1 chosen from 1 choice
thiago@thiago-laptop:~$ 

```lsusb:
```
Bus 002 Device 002: ID 1c4f:0003 SiGma Micro 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04e8:1f03 Samsung Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

