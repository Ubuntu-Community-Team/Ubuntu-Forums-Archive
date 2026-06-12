---
title: "Twinhan USB IR not responding"
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jbman on 2010-04-12
Hi guys,

I just upgraded from 8.04 to 10.04 B2

Everything is going well so far however my Twinhan USB IR is showing as attached, flashing when I press my remote, but not registering any key presses when connected to 10.04 beta 2.

I hooked it up to my 9.04 machine just to be sure and it worked right away.

The Twinhan USB IR comes up as a keyboard so lirc isn't needed as each button is just a keypress. I like it this way so I don't have any other configuration to do.

 hid_twinhan & usbhid are the two modules that are loaded when I plug the usb IR in. I have tried booting with it plugged in and without same deal.

lsusb
Bus 004 Device 002: ID 6253:0100 TwinHan Technology Co., Ltd Ir reciver f. remote control

messages.log
Apr 12 19:21:10 mythtv kernel: [ 1647.210396] input: Twinhan Tech Remote Control as /devices/pci0000:00/0000:00:04.0/usb4/4-1/4-1:1.0/input/input11
Apr 12 19:21:10 mythtv kernel: [ 1647.210508] twinhan 0003:6253:0100.0005: input,hidraw0: USB HID v1.10 Keyboard [Twinhan Tech Remote Control] on usb-0000:00:04.0-1/input0
Apr 12 19:21:10 mythtv kernel: [ 1647.221379] input: Twinhan Tech Remote Control as /devices/pci0000:00/0000:00:04.0/usb4/4-1/4-1:1.1/input/input12
Apr 12 19:21:10 mythtv kernel: [ 1647.221514] twinhan 0003:6253:0100.0006: input,hidraw1: USB HID v1.10 Mouse [Twinhan Tech Remote Control] on usb-0000:00:04.0-1/input1

Any ideas would be appreciated.

Thanks in advance.

---

