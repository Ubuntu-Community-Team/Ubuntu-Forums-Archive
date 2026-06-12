---
title: "dell mini 1012 lucid update borked touchpad."
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jalirious on 2010-03-31
Hi, today's update (31/3/10) of lucid has played silly buggers with my Dell inspiron mini 10 (1012) touchpad.

No tap-to-click functionality, no scrolling, jumpy, amphetamine mouse even on the slowest sensitivity and acceleration settings. Every time I use the integrated touchpad mouse buttons to click they jump at the contact (resorted to using a biro to click :/).

I know lucid is still in beta - is anyone aware of a workaround before this is fixed in the final release?

Regards, Ben.

---

### Post by zustimmung2 on 2010-03-31
Hello,

i also updated my Dell Mini Inspiron 1012 this morning and ended up with the touchpad symptoms described above. Would be great to find a way to fix that.

Here some more infomation on the hardware (dmesg):

[   20.442862] Synaptics Touchpad, model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04711/0xa40000
[   20.517489] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8

Update:
Looks like the Dell 10v is also having the same problem:
[http://www.mail-archive.com/ubuntu-x-swat@lists.launchpad.net/msg57560.html]("http://www.mail-archive.com/ubuntu-x-swat@lists.launchpad.net/msg57560.html")

Update:
This is a recently reported Bug and seems to get fixed soon:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/552317]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/552317")

---

### Post by jalirious on 2010-03-31
An update and reboot - business as usual. Stirling work Alberto.

---

