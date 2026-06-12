---
title: "help w/udev rule for Cirque Glidepoint?"
date: 2011-11-18
forum: Installation &amp; Upgrades
---

### Post by nsqtr on 2011-11-18
Folks,  I've got an Adesso keyboard with a Cirque Glidepoint touchpad.

Cirque is a subsidiary of Alps, although that doesn't specifically mean that Cirque's Glidepoint is compatible with the alps touchpad driver.

Nonetheless, I'm plowing forward. Between Xorg.log and the output of udevadm, I think I've got enough information to wire up the Glidepoint to the synaptic driver, assuming I can write a udev rule for inclusion in /etc/udev/rules.d.

But I cannot find a simple explanation or example of writing such a rule.  Teasing out the salient part of /lib/udev/rules.d/60-persistent-input.rules and /lib/udev/rules.d/66-xorg-synaptics-quirks.rules  has been unproductive.

Can someone point me to a good source?

If I can at least wire up the rules, I can play around with different drivers.

I think I need to tell X to use a specific driver, rather than evdev, since I want to get access to seemingly vendor-specific capabilities -- which might be available through the synaptics driver.

thanks for any help. Output of udevadm and Xorg.log are below.

Using udevadm, I've lifted:


  looking at device '/devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.5/1-2.5:1.0/input/input3/event3':
    KERNEL=="event3"
    SUBSYSTEM=="input"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.5/1-2.5:1.0/input/input3':
    KERNELS=="input3"
    SUBSYSTEMS=="input"
    DRIVERS==""
    ATTRS{name}=="Cirque GlidePoint"
    ATTRS{phys}=="usb-0000:00:02.1-2.5/input0"
    ATTRS{uniq}==""
    ATTRS{properties}=="0"

and Xorg.log shows me:

[    26.124] (II) config/udev: Adding input device Cirque GlidePoint (/dev/input/event3)
[    26.125] (**) Cirque GlidePoint: Applying InputClass "evdev pointer catchall"
[    26.125] (**) Cirque GlidePoint: Applying InputClass "evdev keyboard catchall"
[    26.125] (II) Using input driver 'evdev' for 'Cirque GlidePoint'
[    26.125] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.125] (**) Cirque GlidePoint: always reports core events
[    26.125] (**) Cirque GlidePoint: Device: "/dev/input/event3"
[    26.125] (--) Cirque GlidePoint: Found 3 mouse buttons
[    26.125] (--) Cirque GlidePoint: Found scroll wheel(s)
[    26.125] (--) Cirque GlidePoint: Found relative axes
[    26.125] (--) Cirque GlidePoint: Found x and y relative axes
[    26.125] (--) Cirque GlidePoint: Found absolute axes
[    26.125] (II) evdev-grail: failed to open grail, no gesture support
[    26.125] (--) Cirque GlidePoint: Found keys
[    26.125] (II) Cirque GlidePoint: Configuring as mouse
[    26.125] (II) Cirque GlidePoint: Configuring as keyboard
[.... and much more...

---

### Post by nsqtr on 2011-11-19
sorry, I forgot to mention that I'm running 11.10

---

