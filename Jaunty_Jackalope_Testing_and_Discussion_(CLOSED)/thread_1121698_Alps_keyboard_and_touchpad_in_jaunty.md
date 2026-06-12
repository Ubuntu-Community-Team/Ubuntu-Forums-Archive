---
title: "Alps keyboard and touchpad in jaunty"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by combuster on 2009-04-10
I have Dell Vostro 1310 laptop and my keyboard and touchpad are not repsponding after first boot. It loads gdm but i cant login because i cant type my username/pass. When I plug in logitech pro2400 deskset and reset jaunty everything works fine, so the problem is occuring only when i turn on my laptop for the first time. Here is some relevant output:

[    2.411956] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    4.164456] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[   11.091427] input: Logitech 2.4GHz Cordless Desktop as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input8
[   11.206092] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   11.137192] logitech 0003:046D:C512.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech 2.4GHz Cordless Desktop] on usb-0000:00:1d.0-2/input0
[   11.173873] input: Logitech 2.4GHz Cordless Desktop as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.1/input/input9
[   11.217329] logitech 0003:046D:C512.0002: input,hiddev96,hidraw1: USB HID v1.11 Mouse [Logitech 2.4GHz Cordless Desktop] on usb-0000:00:1d.0-2/input1
[   12.078615] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input10
[   12.145592] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input11

This is after I restart jaunty.

I guess that because of boot time optimization the kernel won't wait for my touchpad to initialize and so it's not recognized, but after restart everything is ok. That gives me a great deal of trouble because i can't carry my wireless deskset everywhere i go and i will not be able to log in or shutdown the laptop. Does anybody else have this problem? How to fix it? The same problem is occuring in Fedora 11 beta but in Arch it's ok. What is the problem, should i wait for kernel update to fix this or there is another way.

---

### Post by combuster on 2009-04-11
[https://bugs.launchpad.net/ubuntu/+bug/359480](https://bugs.launchpad.net/ubuntu/+bug/359480)

Any suggestions?

---

