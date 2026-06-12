---
title: "(lucid) SynPS/2 Synaptics TouchPad suddenly stopped working"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Jarige on 2010-04-10
I watched some movie using VLC this morning, and I suddenly noticed my keyboard and touchpad were not responding anymore. I couldn't do anything, but going to tty1 worked as usual. I rebooted, and got my keyboard back, but my touchpad is still not working. I plugged in an usb mouse, which works as it should work.

I checked dmesg and it does list my touchpad under input9. This is about the SynPS/2 Synaptics TouchPad. It happened on Lucid, using my Acer Aspire One ZG5.

dmesg says the following about the touchpad:

```

[    4.436700] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04771/0xa40000
[    4.536280] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input9


```


I got this command for extra info:
```

name@name:~$ xinput list-props "SynPS/2 Synaptics TouchPad"
Device 'SynPS/2 Synaptics TouchPad':
	Device Enabled (132):	1
	Device Accel Profile (254):	0
	Device Accel Constant Deceleration (255):	1.000000
	Device Accel Adaptive Deceleration (257):	1.000000
	Device Accel Velocity Scaling (258):	10.000000
	Synaptics Edges (272):	1752, 5192, 1620, 4236
	Synaptics Finger (273):	24, 29, 255
	Synaptics Tap Time (274):	180
	Synaptics Tap Move (275):	221
	Synaptics Tap Durations (276):	180, 180, 100
	Synaptics Tap FastTap (277):	0
	Synaptics Middle Button Timeout (278):	75
	Synaptics Two-Finger Pressure (279):	280
	Synaptics Two-Finger Width (280):	7
	Synaptics Scrolling Distance (281):	100, 100
	Synaptics Edge Scrolling (282):	1, 1, 0
	Synaptics Two-Finger Scrolling (283):	0, 0
	Synaptics Move Speed (284):	0.400000, 0.700000, 0.009952, 40.000000
	Synaptics Edge Motion Pressure (285):	29, 159
	Synaptics Edge Motion Speed (286):	1, 401
	Synaptics Edge Motion Always (287):	0
	Synaptics Button Scrolling (288):	1, 1
	Synaptics Button Scrolling Repeat (289):	1, 1
	Synaptics Button Scrolling Time (290):	100
	Synaptics Off (291):	0
	Synaptics Guestmouse Off (292):	0
	Synaptics Locked Drags (293):	0
	Synaptics Locked Drags Timeout (294):	5000
	Synaptics Tap Action (295):	2, 3, 0, 0, 1, 3, 2
	Synaptics Click Action (296):	1, 1, 1
	Synaptics Circular Scrolling (297):	0
	Synaptics Circular Scrolling Distance (298):	0.100000
	Synaptics Circular Scrolling Trigger (299):	0
	Synaptics Circular Pad (300):	0
	Synaptics Palm Detection (301):	0
	Synaptics Palm Dimensions (302):	10, 199
	Synaptics Coasting Speed (303):	0.000000
	Synaptics Pressure Motion (304):	29, 159
	Synaptics Pressure Motion Factor (305):	1.000000, 1.000000
	Synaptics Grab Event Device (306):	1
	Synaptics Gestures (307):	1
	Synaptics Capabilities (308):	1, 1, 1, 0, 0
	Synaptics Pad Resolution (309):	182, 121
	Synaptics Area (310):	0, 0, 0, 0
	Synaptics Jumpy Cursor Threshold (311):	0


```

I tried reinstalling xserver-xorg-input-synaptics. I tried completely removing the package, rebooting, installing, rebooting and it didn't work. Removing the package did make the touchpad work very annoyingly though. Coudn't tap to click, and it was very, very sensitive. It probably used some other driver I suppose. And of course, I tried Fn + F7 to activate or deactivate the touchpad.

Does anyone know how to make it work again?

---

### Post by Jarige on 2010-04-11
bump and some extra information.
I can get my mousepad working perfectly when in the login screen. It works just as I used to work with it, and when pressing enter to log in, it works for a little while. I keep on rubbing that little touchpad, but eventually it stops before the gnome panels appear, before I stopped rubbing.

So it has got to be some configuration file that went wrong somewhere, somehow. I'll check some of the maps in /home but I hope to hear from anyone soon!

---

### Post by Jarige on 2010-04-11
The following log is from Xorg.0.log
I hope this might say more:

```

(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event8"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event4)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event4"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)

```

I hope this might come in handy...

---

### Post by zoffi on 2010-04-16
I have the exact same problem on my Acer Aspire 5920G. My mousepad works in the login screen, but "freezes" before gnome is ready. I've hit Fn+F7, which shows that I'm actually disabling the mousepad. So I hit it again making sure it's turned on even though it still don't work. Now typing CTRL+ALT+backspace brings me back to the login screen, ofc the mousepad works here as before. After a couple of tries it works in gnome to. This started after the update a few days ago.

---

### Post by Jarige on 2010-04-16
There's a bug report that reports this:
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/549727]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/549727")

For me, it's already solved however. I'll mark this topic solved, I forgot about this topic. I don't know why, but I think a new gdm version solved this... At least for me it did.

If you ever need me for debugging or something, contact me here.

---

### Post by bigcrunch on 2010-04-25
You can write:
```
sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps

```

To make permanet include the last line in /etc/modprobe.d/options

---

### Post by Jarige on 2010-04-25
Thank you, bigcrunch :)

Although this bug is somehow fixed for me, this might help other people. I'll post this as a possible workaround at the bug report.

---

