---
title: "input,hidraw0: USB HID v1.11 Keyboard"
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2008-06-02
My pc uses Ubuntu 8.04 with a PS/2 keyboard.

I got a Yubikey, which is a USB keybard. I found in dmesg:
> Jun  2 17:08:32 ronald-desktop kernel: [59074.144690] usb 2-5.1: new low speed USB device using ehci_hcd and address 11
Jun  2 17:08:32 ronald-desktop kernel: [59074.263445] usb 2-5.1: configuration #1 chosen from 1 choice
Jun  2 17:08:32 ronald-desktop kernel: [59074.285243] input: Yubico Yubico Yubikey Touch as /devices/pci0000:00/0000:00:02.1/usb2/2-5/2-5.1/2-5.1:1.0/input/input8
Jun  2 17:08:33 ronald-desktop kernel: [59074.311719] input,hidraw0: USB HID v1.11 Keyboard [Yubico Yubico Yubikey Touch] on usb-0000:00:02.1-5.1

and "sudo lsinput" shows
> /dev/input/event7
   bustype : BUS_USB
   vendor  : 0x1050
   product : 0x10
   version : 273
   name    : "Yubico Yubico Yubikey Touch"
   phys    : "usb-0000:00:02.1-5.1/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_MSC EV_LED EV_REP


How can I use my keyboard (PS/2) ***AND*** the USB keyboard at the same time?

bye

Ronald

---

### Post by ELMIT on 2008-06-02
It works, I just tried a defect one first!

---

