---
title: "Infinite loop prevents from booting Ubuntu 11.10 after clean install"
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by Panna-cakkhu on 2011-10-24
I did a clean install of Ubuntu 11.10 and only ended up in a black screen at boot time. After removing the "quiet splash" options to see command prompts it seems i cannot login due to an infinite loop regarding the detection of my USB mouse. 

```
[   ...  ] ...
[  29.33 ] eth0: no IPv6 routers present
[  32.29 ] wlan0: no IPv6 routers present
[  **60.16** ] usb 2-1.6: USB disconnect, **device number 6**
[  61.64 ] usb 2-1.6: new low speed **USB device number 7** using ehci_hcd
[  61.74 ] input: PixArt USB Optical Mouse as as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/**input11**
[  61.75 ] generic-usb 0003:093A:2510.**0004**: input,hidraw2: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:1d.0-1.6/input0
[ **109.77** ] usb 2-1.6: USB disconnect, **device number 7**
[ 111.25 ] usb 2-1.6: new low speed **USB device number 8** using ehci_hcd
[ 111.36 ] input: PixArt USB Optical Mouse as as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/**input12**
[ 111.37 ] generic-usb 0003:093A:2510.**0005**: input,hidraw2: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:1d.0-1.6/input0
[ **159.39** ] usb 2-1.6: USB disconnect, **device number 8**
[ 160.87 ] usb 2-1.6: new low speed **USB device number 9** using ehci_hcd
[ 160.97 ] input: PixArt USB Optical Mouse as as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/**input13**
[ 160.98 ] generic-usb 0003:093A:2510.**0006**: input,hidraw2: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:1d.0-1.6/input0
[   ...  ] ...
```

I have both a USB keyboard and USB mouse. If i switch them the infinite loop is then with respect to the USB keyboard...

From the live CD, i tried both the options "deleting and reinstalling Ubuntu 11.10" and "Upgrading from 11.10 to 11.10" (seemed to have fixed some issues for others) but without success.

Any help would be greatly appreciated

---

### Post by pastalavista on 2011-10-24
Did you try booting without the mouse attached and then adding it after you log in? Then log out and back in with them both attached and it should remember the configuration.

---

### Post by Panna-cakkhu on 2011-10-25
I found out that these messages were only there because the boot process was hanging. The real problem was my graphic card. Still not resolved but i'll create a new thread for that...

---

