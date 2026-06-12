---
title: "X crashing"
date: 2010-03-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Rob2687 on 2010-03-03
Xorg seems to be crashing randomly. I can't find the cause of the problem. It occurs a few times a day when I'm using Lucid. When it crashes I get thrown back to the GDM login.

I've tried to run apport-bug but I'm not sure which package to use. I've tried apport xserver-xorg and xserver-xorg-core but it always ends up filing it under nvidia-graphics-drivers so I haven't submitted any bug report yet. I am using the open source ATI driver.

```
(II) XINPUT: Adding extended input device ""AT Translated Set 2 keyboard"" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device "SynPS/2 Synaptics TouchPad" (/dev/input/event5)
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.7.3.901, module version = 1.2.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.0
(**) Option "Device" "/dev/input/event5"
(II) "SynPS/2 Synaptics TouchPad": x-axis range 1472 - 5472
(II) "SynPS/2 Synaptics TouchPad": y-axis range 1408 - 4448
(II) "SynPS/2 Synaptics TouchPad": pressure range 0 - 255
(II) "SynPS/2 Synaptics TouchPad": finger width range 0 - 0
(II) "SynPS/2 Synaptics TouchPad": buttons: left right middle double triple
(--) "SynPS/2 Synaptics TouchPad": touchpad found
(**) "SynPS/2 Synaptics TouchPad": always reports core events
(II) XINPUT: Adding extended input device ""SynPS/2 Synaptics TouchPad"" (type: TOUCHPAD)
(**) "SynPS/2 Synaptics TouchPad": (accel) keeping acceleration scheme 1
(**) "SynPS/2 Synaptics TouchPad": (accel) acceleration profile 0
(--) "SynPS/2 Synaptics TouchPad": touchpad found
(II) config/udev: Adding input device "SynPS/2 Synaptics TouchPad" (/dev/input/mouse1)
(**) "SynPS/2 Synaptics TouchPad": always reports core events
(**) "SynPS/2 Synaptics TouchPad": Device: "/dev/input/mouse1"
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for ""SynPS/2 Synaptics TouchPad""
(II) config/udev: Adding input device "PS/2 Generic Mouse" (/dev/input/event7)
(**) "PS/2 Generic Mouse": always reports core events
(**) "PS/2 Generic Mouse": Device: "/dev/input/event7"
(II) "PS/2 Generic Mouse": Found 3 mouse buttons
(II) "PS/2 Generic Mouse": Found relative axes
(II) "PS/2 Generic Mouse": Found x and y relative axes
(II) "PS/2 Generic Mouse": Configuring as mouse
(**) "PS/2 Generic Mouse": YAxisMapping: buttons 4 and 5
(**) "PS/2 Generic Mouse": EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device ""PS/2 Generic Mouse"" (type: MOUSE)
(**) "PS/2 Generic Mouse": (accel) keeping acceleration scheme 1
(**) "PS/2 Generic Mouse": (accel) acceleration profile 0
(II) "PS/2 Generic Mouse": initialized for relative axes.
(II) config/udev: Adding input device "PS/2 Generic Mouse" (/dev/input/mouse2)
(**) "PS/2 Generic Mouse": always reports core events
(**) "PS/2 Generic Mouse": Device: "/dev/input/mouse2"
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for ""PS/2 Generic Mouse""
(II) config/udev: Adding input device "Macintosh mouse button emulation" (/dev/input/event3)
(**) "Macintosh mouse button emulation": always reports core events
(**) "Macintosh mouse button emulation": Device: "/dev/input/event3"
(II) "Macintosh mouse button emulation": Found 3 mouse buttons
(II) "Macintosh mouse button emulation": Found relative axes
(II) "Macintosh mouse button emulation": Found x and y relative axes
(II) "Macintosh mouse button emulation": Configuring as mouse
(**) "Macintosh mouse button emulation": YAxisMapping: buttons 4 and 5
(**) "Macintosh mouse button emulation": EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device ""Macintosh mouse button emulation"" (type: MOUSE)
(**) "Macintosh mouse button emulation": (accel) keeping acceleration scheme 1
(**) "Macintosh mouse button emulation": (accel) acceleration profile 0
(II) "Macintosh mouse button emulation": initialized for relative axes.
(II) config/udev: Adding input device "Macintosh mouse button emulation" (/dev/input/mouse0)
(**) "Macintosh mouse button emulation": always reports core events
(**) "Macintosh mouse button emulation": Device: "/dev/input/mouse0"
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for ""Macintosh mouse button emulation""

Fatal server error:
failed to map pixmap -85


Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(II) "Power Button": Close
(II) UnloadModule: "evdev"
(II) "Video Bus": Close
(II) UnloadModule: "evdev"
(II) "Sleep Button": Close
(II) UnloadModule: "evdev"
(II) "AT Translated Set 2 keyboard": Close
(II) UnloadModule: "evdev"
(II) UnloadModule: "synaptics"
(II) "PS/2 Generic Mouse": Close
(II) UnloadModule: "evdev"
(II) "Macintosh mouse button emulation": Close
(II) UnloadModule: "evdev"
(II) AIGLX: Suspending AIGLX clients for VT switch
 ddxSigGiveUp: Closing log
```

---

