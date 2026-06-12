---
title: "Touch screen cannot install reliable."
date: 2013-04-15
forum: Installation &amp; Upgrades
---

### Post by mensfort on 2013-04-15
I had problems with Beetronics monitors 10" touch, running an Egalax driver. Because of this, I try to change from Linux Mint 10 to Xubuntu, Ubuntu or whatever Linux is working for me.
Xubuntu can calibrate the touch screen, which I like in the user-interface. It seems very user-friendly, but is not working and therefore useless. 


Sometimes the settings are not used. Sometimes it works for a few days and sometimes scaling is completely wrong after a reboot.

- When I install xinput_calibrator, do the calibration and create file /usr/share/X11/xorg.conf.d/99-settings.conf , this is usually working a few days.
- Also, I need to have to change a line into: /etc/default/grub  and do sudo update-grub2
  GRUB_CMDLINE_LINUX_DEFAULT="18042.noloop=1 usbhid.quirks=0xeef:0x1:0x40"


When I do : xrandr --output DVI1 --mode 800x600 inside ~/.xprofile  then the scaling may go wrong completely...

Please help, until now I only get stability in Linux Mint 11 but then I also needed some udev rules. This gives Linux a bad name and is not user-friendly at all! This problem happens at 4 of my customers.

Herre is something wrong in Xorg.conf probably:
[    15.316] (II) config/udev: Adding input device eGalax Inc. USB TouchController (/dev/input/event8)
[    15.316] (**) eGalax Inc. USB TouchController: Applying InputClass "evdev tablet catchall"
[    15.316] (II) Using input driver 'evdev' for 'eGalax Inc. USB TouchController'
[    15.316] (**) eGalax Inc. USB TouchController: always reports core events
[    15.316] (**) evdev: eGalax Inc. USB TouchController: Device: "/dev/input/event8"
[    15.317] (--) evdev: eGalax Inc. USB TouchController: Vendor 0xeef Product 0x1
[    15.317] (--) evdev: eGalax Inc. USB TouchController: Found absolute axes
[    15.317] (--) evdev: eGalax Inc. USB TouchController: Found x and y absolute axes
[    15.317] (--) evdev: eGalax Inc. USB TouchController: Found absolute tablet.
[    15.317] (II) evdev: eGalax Inc. USB TouchController: Configuring as tablet
[    15.317] (**) evdev: eGalax Inc. USB TouchController: YAxisMapping: buttons 4 and 5
[    15.317] (**) evdev: eGalax Inc. USB TouchController: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    15.317] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input8/event8"
[    15.317] (II) XINPUT: Adding extended input device "eGalax Inc. USB TouchController" (type: TABLET, id 12)
[    15.317] (II) evdev: eGalax Inc. USB TouchController: initialized for absolute axes.
[    15.318] (**) eGalax Inc. USB TouchController: (accel) keeping acceleration scheme 1
[    15.318] (**) eGalax Inc. USB TouchController: (accel) acceleration profile 0
[    15.318] (**) eGalax Inc. USB TouchController: (accel) acceleration factor: 2.000

feel free to help, thanks ahead!

---

