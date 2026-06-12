---
title: "How to properly make udev rule for touchscreen ?"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by rrozman on 2008-01-31
Hi,

I have Touchscreen from General Touch company... I had this device working under Debian, and I' m now struggling to get it working under Kubuntu 710.

Under Debian it was enough to put this rule into /etc/udev/rules.d :

```
BUS=="usb", KERNEL=="event[0-3]*", SYSFS{product}=="GeneralTouch USB Touchscreen", SYMLINK=="input/gtouch"
```

and my touchscreen device always appeared at /dev/input/gtouch. Under KUBUNTU same thing doesn't work. As I see (I don't know Linux so well), rules are now defined in 3 parts : first in 20-names.rules, then in 40-permissions.rules and at last on the spot I was adding my rule before : 60-symlinks.rules .

Currently I'm, getting this in dmesg :

> dmesg | grep input
[   20.699985] input: Macintosh mouse button emulation as /class/input/input0
[   20.752388] input: AT Translated Set 2 keyboard as /class/input/input1
[   33.113212] input: PC Speaker as /class/input/input2
[   34.662851] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
[   35.248511] input: General Touch Co. Ltd.  GeneralTouch USB Touchscreen as /class/input/input4
[   35.248588] input,hiddev96: USB HID v1.10 Mouse [General Touch Co. Ltd.  GeneralTouch USB Touchscreen] on usb-0000:00:1d.7-3.4
[   35.248604] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   53.983763] input: Power Button (FF) as /class/input/input5
[   54.028533] input: Power Button (CM) as /class/input/input6

Does anyone know how to define proper rules, so touchscreen device will always be under it's own device hook ?

Thanks in advance,

regards,

Rob.

---

