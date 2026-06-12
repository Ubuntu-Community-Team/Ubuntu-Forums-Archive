---
title: "Keyboard and Mouse not working 08.04 - 10.04"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by merrik on 2010-11-07
I`ve upgraded from 08.04 to 10.04, everything worked until 09.10, but with 10.04 I can`t get the keyboard and mouse to work, mouse works if I add "AutoAddDevices" "False" to xorg.conf but the keyboard does not, I`ve tried to configure the keyboard to use kbd but I get a error "(EE) No Input driver matching `kbd'". Here is the relevant bit of the Xorg.0.log:

```
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (FF) (/dev/event0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Power Button (CM) (/dev/event1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device USB Optical Mouse (/dev/event3)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device USB Optical Mouse (/dev/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/event4)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/event2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/mouse0)
(II) No input driver/identifier specified (ignoring)
```

I`ve tried add the identifiers to /usr/lib/X11/xorg.conf.d/5-evdev.conf ([link]("http://blog.ichinmay.com/2010/05/03/ubuntu-10-04-upgrade-from-9-10-usb-keyboard-mouse-problem/")) without success, the weird thing is that this works on the live cd ... 

Do I need to change xorg.conf- not using it now -?  Maybe edit a fdi file, or create e udev rule, install a xorg driver, rollback to 09.10, I just want the quickiest solution because this is bothering me all week.

It would be nice if there is a easy way to cleanup what I don`t need anymore from the filesystem, the "computer janitor" didn`t work ...

--------

here is how it looks like using the live cd:
What could possibly be different on this computer from the live-cd that makes the live cd match the "catchall" rules?
Found it, on the live cd it uses "/dev/input/event3" while in the harddisk "/dev/event3", but here is my new rule, it didn`t work either:

```
Section "InputClass"
	Identifier "Dell Dell USB Keyboard"
	MatchIsTouchscreen "on"
	MatchDevicePath "/dev/event*"
	Driver "evdev"
EndSection

Section "InputClass"
	Identifier "USB Optical Mouse"
	MatchIsTouchscreen "on"
	MatchDevicePath "/dev/event*"
	Driver "evdev"
EndSection
```

```
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device USB Optical Mouse (/dev/input/event3)
(**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) USB Optical Mouse: always reports core events
(**) USB Optical Mouse: Device: "/dev/input/event3"
(II) USB Optical Mouse: Found 3 mouse buttons
(II) USB Optical Mouse: Found scroll wheel(s)
(II) USB Optical Mouse: Found relative axes
(II) USB Optical Mouse: Found x and y relative axes
(II) USB Optical Mouse: Configuring as mouse
(**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE)
(II) USB Optical Mouse: initialized for relative axes.
(II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event4)
(**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**) Dell Dell USB Keyboard: always reports core events
(**) Dell Dell USB Keyboard: Device: "/dev/input/event4"
(II) Dell Dell USB Keyboard: Found keys
(II) Dell Dell USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
```

---

### Post by ioargento on 2010-11-26
Same issue over here while upgrading to 10.04 to 10.10!

---

### Post by bryanray on 2010-12-28
Hi,

I've just done a similar upgrade from 8.10 to 10.04, and had a very similar problem if not identical. After some time scrabbling around the X configuration, I realised that /dev/event* had been moved to /dev/input/event*. This told me that the kernel had been upgraded, and that the kernel I was running on was the previous version. There may well be other changes as well...

Once I had re-run the grub configuration, everything was fine.

Bryan

---

