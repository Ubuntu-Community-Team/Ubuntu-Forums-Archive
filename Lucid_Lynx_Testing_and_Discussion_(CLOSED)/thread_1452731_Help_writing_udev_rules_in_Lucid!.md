---
title: "Help writing udev rules in Lucid!"
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by matthewbpt on 2010-04-12
Hey everyone,

I decided to install Lucid and was delighted to find that my touchscreen works out of the box using the **usbtouchscreen** drive along with **evdev**. One problem however was that the calibration was way off and the axes were inverted. I compiled and installed a program called xinput_calibrator, which does a four point calibration and then dynamically calibrates the screen using xinput. This is great except that the changed are not made permanent, so calibration needs to be done on every reboot or restart of X. The program however does print instructions on how to make it permanent using udev and xorg.conf . I know xorg.conf is deprecated so I decided to try udev, this is the output from the program:
```
xxx@xxx:~$ xinput_calibrator_gtkmm 
Calibrating EVDEV driver for "SLT Digital  USB TouchController " id=10
	current calibration values (from XInput): min_x=0, max_x=2047 and min_y=0, max_y=2047

Doing dynamic recalibration:
	Swapping X and Y axis...
	Setting new calibration data: 24, 1961, 1951, 198


== Making the calibration permanent ==
If you have the 'xinput' tool installed, a simple way is to create a script that starts with your X session, containing the following command(s):
    xinput set-int-prop "SLT Digital  USB TouchController " "Evdev Axes Swap" 8 1
    xinput set-int-prop "SLT Digital  USB TouchController " "Evdev Axis Calibration" 32 24 1961 1951 198

If you have evdev version 2.3.0 or higher, there are 2 more ways: the tranditional way (xorg.conf) and the new way (udev rule):
xorg.conf: edit /etc/X11/xorg.conf and add in the 'Section "InputDevice"' of your device:
    Option	"SwapAxes"	"1" # unless it was already set to 1
    Option	"Calibration"		"1958 27 187 1955"
udev rule: create the file '/etc/udev/rules.d/99_touchscreen.rules' with:
    ACTION!="add|change", GOTO="xorg_touchscreen_end"
    KERNEL!="event*", GOTO="xorg_touchscreen_end"
    ATTRS{product}!="SLT Digital  USB TouchController ", GOTO="xorg_touchscreen_end"
    ENV{x11_options.swapxy}="1"
ENV{x11_options.calibration}="1958 27 187 1955"

    LABEL="xorg_touchscreen_end"
```
So I created the file /etc/udev/rules.d/99_touchscreen.rules with
```
    ACTION!="add|change", GOTO="xorg_touchscreen_end"
    KERNEL!="event*", GOTO="xorg_touchscreen_end"
    ATTRS{product}!="SLT Digital  USB TouchController ", GOTO="xorg_touchscreen_end"
    ENV{x11_options.swapxy}="1"
ENV{x11_options.calibration}="1958 27 187 1955"

    LABEL="xorg_touchscreen_end"
```
and rebooted but it had no effect whatsoever, I still need to recalibrate the screen. Any ideas about what I'm doing wrong writing the udev rule?

Cheers,

Matt

---

### Post by Zorael on 2010-04-12
Tagging thread for interest (since I also had some issues writing my own udev rule).

Do note that you can also use the xinput command that's listed there. You could create a script of it and place a reference to that in Xsetup, to be run before gdm loads the greeter. Or just in your autostart directory and have it take effect after logging in.

```
#!/bin/bash

xinput set-int-prop "SLT Digital  USB TouchController " "Evdev Axes Swap" 8 1
xinput set-int-prop "SLT Digital  USB TouchController " "Evdev Axis Calibration" 32 24 1961 1951 198
```

Check the output of 'xinput list' and verify the device string is "SLT Digital  USB TouchController " as listed.

But obviously, an udev rule is a neater solution.

---

### Post by matthewbpt on 2010-04-13
That would work if I put it in the Xsetup, but I'm not satisfied with this solution because when I disable the touchscreen to save battery power, the module for it gets unloaded and when I re-enable it it has lost its calibration so I have to run the xinput commands again. A udev rule would automatically apply the calibration whenever the device is loaded. I'll use your solution for now, but I really want to sort udev out. Thanks for the help :)

---

### Post by tormod on 2010-04-13
I would not say xorg.conf is deprecated, lucid has even support for an xorg.conf.d/ directory. See for instance [http://who-t.blogspot.com/2010/01/new-configuration-world-order.html](http://who-t.blogspot.com/2010/01/new-configuration-world-order.html) and [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=572692](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=572692) or [https://launchpad.net/bugs/430532](https://launchpad.net/bugs/430532)

See also [https://wiki.ubuntu.com/X/InputConfiguration](https://wiki.ubuntu.com/X/InputConfiguration) for information on xorg udev rules. To check udev rules in general you can try "udevadm test /devices/..." where you can find the correct /devices/... path for instance by looking through /var/log/udev .

I am afraid I can not give any specific help in this case, but if the rules are correctly triggered I would wonder if the option names are correct, namely "swapxy" and "calibration". I think they will show up as "Option" lines in Xorg.0.log if they are handed correctly from udev to the xserver. The spelling for the xorg.conf options is "SwapAxes" and "Calibration". But I don't know if all options are handed over...

---

### Post by tormod on 2010-04-13
Forget about that wiki page, it was not up to date for Lucid (I added a note to it now). The x11_option.foo is not supported in Lucid. So xorg.conf.d is the way to go.

---

### Post by matthewbpt on 2010-04-13
I really like the xorg.conf.d solutuon, it looks much simpler than making a udev rule and work just as well. Thanks for the tip! I'll try it tomorrow as I'm going to bed now. In the meantime anyone know how to configure an evdev touchscreen to emulate a right click? I can't seem to find anything on google...

Cheers :)

---

