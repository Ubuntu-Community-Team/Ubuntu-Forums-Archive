---
title: "Mouse doesn't work [Kubuntu 9.10 Alpha 3]"
date: 2009-07-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by QueenZ on 2009-07-24
My USB Mouse worked ok in Live CD but when I installed that system it doesn't work anymore.. Is there anything i can do to get it work?

---

### Post by Soul-Sing on 2009-07-24
What is the outcome of:
```
lsusb
```

---

### Post by John Deer on 2009-08-29
My usb mouse is also not working. I'm on Kubuntu 9.10 latest update to this day.


lsusb
Bus 007 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 007 Device 003: ID 056a:0093 Wacom Co., Ltd         
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub                  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub                  
Bus 003 Device 002: ID 0f62:1001 Acrox Technologies Co., Ltd Targus Mini Trackball Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub                                  
Bus 006 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub                                            
Bus 005 Device 003: ID 1267:0103 Logic3 / SpectraVideo plc G-720 Keyboard                                 
Bus 005 Device 002: ID 058f:9254 Alcor Micro Corp. Hub                                                    
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub                                            
Bus 002 Device 003: ID 064e:a104 Suyin Corp.                                                              
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by John Deer on 2009-09-09
The problem appears to be that the Wacom (touch screen) is taking up all the /dev/eventX char devices. How do I increase the number of /dev/eventX items or how do I prevent the wacom from being initialized (even though it seems to be configured, it is also not working)


Here is the error from the Xorg.0.log
(EE) Too many input devices. Ignoring Acrox USB & PS/2 Mouse


and here is snip-it of everything above
(**) Wacom ISDv4 93 pad: max y set to 16420 by xorg.conf
(**) Wacom ISDv4 93 pad: max z = 255
(**) /dev/input/event11: Touch is enabled
(**) Option "BaudRate" "9600"
(**) Wacom ISDv4 93 pad: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom ISDv4 93 pad" (type: Wacom Pad)
(==) Wacom device "Wacom ISDv4 93 pad" top X=0 top Y=0 bottom X=26212 bottom Y=16420 resol X=2540 resol Y=2540
(II) config/hal: Adding input device Wacom ISDv4 93 pad
(**) Wacom ISDv4 93 pad: always reports core events
(**) Wacom ISDv4 93 pad device is /dev/input/event10
(**) Wacom ISDv4 93 pad is in relative mode
(**) WACOM: suppress value is 2
(**) Wacom ISDv4 93 pad: reading USB link
(**) Wacom ISDv4 93 pad: threshold = 15
(**) Wacom ISDv4 93 pad: max x set to 26202 by xorg.conf
(**) Wacom ISDv4 93 pad: max y set to 16325 by xorg.conf
(**) Wacom ISDv4 93 pad: max z = 255
(**) /dev/input/event10: Touch is enabled
(**) Option "BaudRate" "9600"
(**) Wacom ISDv4 93 pad: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom ISDv4 93 pad" (type: Wacom Pad)
(==) Wacom device "Wacom ISDv4 93 pad" top X=0 top Y=0 bottom X=26202 bottom Y=16325 resol X=2540 resol Y=2540
(II) config/hal: Adding input device Wacom ISDv4 93 cursor
(**) Wacom ISDv4 93 cursor: always reports core events
(**) Wacom ISDv4 93 cursor device is /dev/input/event11
(**) Wacom ISDv4 93 cursor is in relative mode
(**) WACOM: suppress value is 2
(**) Wacom ISDv4 93 cursor: reading USB link
(**) Wacom ISDv4 93 cursor: threshold = 15
(**) Wacom ISDv4 93 cursor: max x set to 26212 by xorg.conf
(**) Wacom ISDv4 93 cursor: max y set to 16420 by xorg.conf
(**) Wacom ISDv4 93 cursor: max z = 255
(**) /dev/input/event11: Touch is enabled
(**) Option "BaudRate" "9600"
(**) Wacom ISDv4 93 cursor: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom ISDv4 93 cursor" (type: Wacom Cursor)
(==) Wacom device "Wacom ISDv4 93 cursor" top X=0 top Y=0 bottom X=26212 bottom Y=16420 resol X=2540 resol Y=2540
(II) config/hal: Adding input device Wacom ISDv4 93 cursor

Wacom ISDv4 93 Wacom X driver grabbed event device
(**) /dev/input/event10: Touch is enabled
(**) /dev/input/event10: Tablet PC buttons are on
(==) Wacom using pressure threshold of 15 for button 1
(==) Wacom USB TabletPC tablet speed=9600 (38400) maxX=26202 maxY=16325 maxZ=255 resX=2540 resY=2540  tilt=disabled
(==) Wacom device "Wacom ISDv4 93" top X=0 top Y=0 bottom X=26202 bottom Y=16325 resol X=2540 resol Y=2540
(II) config/hal: Adding input device HID 1267:0103
(**) HID 1267:0103: always reports core events
(**) HID 1267:0103: Device: "/dev/input/event9"
(II) HID 1267:0103: Found 1 mouse buttons
(II) HID 1267:0103: Found scroll wheel(s)
(II) HID 1267:0103: Found keys
(II) HID 1267:0103: Configuring as keyboard
(II) HID 1267:0103: Adding scrollwheel support
(**) HID 1267:0103: YAxisMapping: buttons 4 and 5
(**) HID 1267:0103: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "HID 1267:0103" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(EE) HID 1267:0103: failed to initialize for relative axes.
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Wacom ISDv4 93 pad
(**) Wacom ISDv4 93 pad: always reports core events
(**) Wacom ISDv4 93 pad device is /dev/input/event11
(**) Wacom ISDv4 93 pad is in relative mode
(**) WACOM: suppress value is 2
(**) Wacom ISDv4 93 pad: reading USB link
(**) Wacom ISDv4 93 pad: threshold = 15

(**) Wacom ISDv4 93 pad: max y set to 16420 by xorg.conf
(**) Wacom ISDv4 93 pad: max z = 255
(**) /dev/input/event11: Touch is enabled
(**) Option "BaudRate" "9600"
(**) Wacom ISDv4 93 pad: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom ISDv4 93 pad" (type: Wacom Pad)
(==) Wacom device "Wacom ISDv4 93 pad" top X=0 top Y=0 bottom X=26212 bottom Y=16420 resol X=2540 resol Y=2540
(II) config/hal: Adding input device Wacom ISDv4 93 pad
(**) Wacom ISDv4 93 pad: always reports core events
(**) Wacom ISDv4 93 pad device is /dev/input/event10
(**) Wacom ISDv4 93 pad is in relative mode
(**) WACOM: suppress value is 2
(**) Wacom ISDv4 93 pad: reading USB link
(**) Wacom ISDv4 93 pad: threshold = 15
(**) Wacom ISDv4 93 pad: max x set to 26202 by xorg.conf
(**) Wacom ISDv4 93 pad: max y set to 16325 by xorg.conf
(**) Wacom ISDv4 93 pad: max z = 255
(**) /dev/input/event10: Touch is enabled
(**) Option "BaudRate" "9600"
(**) Wacom ISDv4 93 pad: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom ISDv4 93 pad" (type: Wacom Pad)
(==) Wacom device "Wacom ISDv4 93 pad" top X=0 top Y=0 bottom X=26202 bottom Y=16325 resol X=2540 resol Y=2540
(II) config/hal: Adding input device Wacom ISDv4 93 cursor
(**) Wacom ISDv4 93 cursor: always reports core events
(**) Wacom ISDv4 93 cursor device is /dev/input/event11
(**) Wacom ISDv4 93 cursor is in relative mode
(**) WACOM: suppress value is 2
(**) Wacom ISDv4 93 cursor: reading USB link
(**) Wacom ISDv4 93 cursor: threshold = 15
(**) Wacom ISDv4 93 cursor: max x set to 26212 by xorg.conf
(**) Wacom ISDv4 93 cursor: max y set to 16420 by xorg.conf
(**) Wacom ISDv4 93 cursor: max z = 255
(**) /dev/input/event11: Touch is enabled
(**) Option "BaudRate" "9600"
(**) Wacom ISDv4 93 cursor: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom ISDv4 93 cursor" (type: Wacom Cursor)
(==) Wacom device "Wacom ISDv4 93 cursor" top X=0 top Y=0 bottom X=26212 bottom Y=16420 resol X=2540 resol Y=2540
(II) config/hal: Adding input device Wacom ISDv4 93 cursor

(**) Wacom ISDv4 93 eraser: always reports core events
(**) Wacom ISDv4 93 eraser device is /dev/input/event11
(**) Wacom ISDv4 93 eraser is in absolute mode
(**) WACOM: suppress value is 2
(**) Wacom ISDv4 93 eraser: reading USB link
(**) Wacom ISDv4 93 eraser: threshold = 15
(**) Wacom ISDv4 93 eraser: max x set to 26212 by xorg.conf
(**) Wacom ISDv4 93 eraser: max y set to 16420 by xorg.conf
(**) Wacom ISDv4 93 eraser: max z = 255
(**) /dev/input/event11: Touch is enabled
(**) Option "BaudRate" "9600"
(**) Wacom ISDv4 93 eraser: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom ISDv4 93 eraser" (type: Wacom Eraser)
(==) Wacom device "Wacom ISDv4 93 eraser" top X=0 top Y=0 bottom X=26212 bottom Y=16420 resol X=2540 resol Y=2540
(II) config/hal: Adding input device Wacom ISDv4 93 eraser
(**) Wacom ISDv4 93 eraser: always reports core events
(**) Wacom ISDv4 93 eraser device is /dev/input/event10
(**) Wacom ISDv4 93 eraser is in absolute mode
(**) WACOM: suppress value is 2
(**) Wacom ISDv4 93 eraser: reading USB link
(**) Wacom ISDv4 93 eraser: threshold = 15
(**) Wacom ISDv4 93 eraser: max x set to 26202 by xorg.conf
(**) Wacom ISDv4 93 eraser: max y set to 16325 by xorg.conf
(**) Wacom ISDv4 93 eraser: max z = 255
(**) /dev/input/event10: Touch is enabled
(**) Option "BaudRate" "9600"
(**) Wacom ISDv4 93 eraser: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom ISDv4 93 eraser" (type: Wacom Eraser)
(==) Wacom device "Wacom ISDv4 93 eraser" top X=0 top Y=0 bottom X=26202 bottom Y=16325 resol X=2540 resol Y=2540
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event4"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)

(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
        compiled for 1.6.3, module version = 1.1.2
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 1.1.2
(**) Option "Device" "/dev/input/event13"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/hal: Adding input device Acrox USB & PS/2 Mouse
(**) Acrox USB & PS/2 Mouse: always reports core events
(**) Acrox USB & PS/2 Mouse: Device: "/dev/input/event7"
(II) Acrox USB & PS/2 Mouse: Found 9 mouse buttons
(II) Acrox USB & PS/2 Mouse: Found x and y relative axes
(II) Acrox USB & PS/2 Mouse: Found scroll wheel(s)
(II) Acrox USB & PS/2 Mouse: Configuring as mouse
(**) Acrox USB & PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) Acrox USB & PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(EE) Too many input devices. Ignoring Acrox USB & PS/2 Mouse
(II) UnloadModule: "evdev"

---

### Post by John Deer on 2009-09-09
Blacklisting the wacom module got the usb mouse working.

added the following line to the bottom of /etc/modprobe.d/blacklist.conf
....

blacklist wacom

....

---

### Post by overdrank on 2009-09-09
Moved to Karmic Koala Testing and Discussion

---

