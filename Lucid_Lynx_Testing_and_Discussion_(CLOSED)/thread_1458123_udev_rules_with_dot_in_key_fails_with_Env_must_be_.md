---
title: "udev rules with dot in key fails with Env must be KEY=VALUE pairs"
date: 2010-04-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by loftux on 2010-04-19
I'm trying to configure my Logitech Marble as per [https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB) documentation.

It runs the rule, but gives the error
```

[13838.180329] usb 7-1: new low speed USB device using uhci_hcd and address 5
[13838.359037] usb 7-1: configuration #1 chosen from 1 choice
[13838.377529] input: Logitech USB Trackball as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input17
[13838.379229] generic-usb 0003:046D:C408.0008: input,hidraw3: USB HID v1.10 Mouse [Logitech USB Trackball] on usb-0000:00:1d.1-1/input0
upstart-udev-bridge[423]	Env must be KEY=VALUE pairs

```

Now if I comment all x11_options like
```
#ENV{x11_options.Buttons}="9"
```
the "Env must be KEY=VALUE pairs" error is gone when plugging in the Logitech mouse.
So I tried to instead removed the dot (.) in the notation above
```
ENV{x11_optionsButtons}="9"
```
and the it works. But of course not the mouse configuration.

My conclusion is that there is a bug in udev when there is a dot in the key for ENV.

---

### Post by SgtPepperKSU on 2010-04-19
From the debian [bugreport](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=576811) that a quick google turned up:

> > Would you please fix it?
> 
No.  x11_options in udev was never a documented or recommended
configuration.  It's gone and will not come back.  Look for
"InputClass" in the xorg.conf manpage for how to set options in
xorg.conf.

---

### Post by loftux on 2010-04-20
Thanks,
Since xorg.conf is no longer used in lucid, it kind of makes it hard to add. And Hal is being deprecated, and now udev rules isn't the way.
I filed a bug on this, [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/567068](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/567068)
Maybe it wont get fixed, but at least it is noted. 

Anyway, I'm trying the shell script solution for 9.10 proposed in the documentation, looks like I can get that to work.

---

### Post by dino99 on 2010-04-20
if lucid dont need xorg.conf by default, most of us have one to tweak settings and special configs

sudo dpkg-reconfigure xserver-xorg

[http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html](http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html)

---

### Post by SgtPepperKSU on 2010-04-20
> **loftux said:**
> Since xorg.conf is no longer used in lucid
That's not true.  It is no longer *required* in most cases since devices are auto-discovered, but it can still be used to change settings.  In fact, an xorg.conf.d directory is now supported to make it easier to isolate and organize xorg.conf settings.

It makes perfect sense to me that the correct place for X11 options would be in the X11 config file(s).  It sounds like that is what you should use.

---

