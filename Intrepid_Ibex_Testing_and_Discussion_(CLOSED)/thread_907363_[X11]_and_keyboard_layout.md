---
title: "[X11] and keyboard layout"
date: 2008-09-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by watchwolf on 2008-09-01
hello :)

I have updated from hardy to intrepid and I have a problem with my keyboard layout, xorg use a us layout but I need a fr layout.
I have configured my xorg.conf but x11 seems create his own configuration for the keyboard :/. 


> (**) Logitech Logitech Dual Action: always reports core events
(**) Logitech Logitech Dual Action: Device: "/dev/input/event5"
(II) Logitech Logitech Dual Action: Found x and y absolute axes
(WW) Logitech Logitech Dual Action: Don't know how to use device
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Logitech Logitech Dual Action"
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "base"
(**) Logitech USB Receiver: xkb_rules: "base"
(**) Option "xkb_model" "evdev"
(**) Logitech USB Receiver: xkb_model: "evdev"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: xkb_layout: "us"
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event3"
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found mouse buttons
(II) Logitech USB Receiver: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(II) config/hal: Adding input device LITEON Technology USB Multimedia Keyboard
(**) LITEON Technology USB Multimedia Keyboard: always reports core events
(**) LITEON Technology USB Multimedia Keyboard: Device: "/dev/input/event2"
(II) LITEON Technology USB Multimedia Keyboard: Found keys
(II) LITEON Technology USB Multimedia Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "LITEON Technology USB Multimedia Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "base"
(**) LITEON Technology USB Multimedia Keyboard: xkb_rules: "base"
(**) Option "xkb_model" "evdev"
(**) LITEON Technology USB Multimedia Keyboard: xkb_model: "evdev"
(**) Option "xkb_layout" "us"
(**) LITEON Technology USB Multimedia Keyboard: xkb_layout: "us"
(II) config/hal: Adding input device LITEON Technology USB Multimedia Keyboard
(**) LITEON Technology USB Multimedia Keyboard: always reports core events
(**) LITEON Technology USB Multimedia Keyboard: Device: "/dev/input/event1"
(II) LITEON Technology USB Multimedia Keyboard: Found keys
(II) LITEON Technology USB Multimedia Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "LITEON Technology USB Multimedia Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "base"
(**) LITEON Technology USB Multimedia Keyboard: xkb_rules: "base"
(**) Option "xkb_model" "evdev"
(**) LITEON Technology USB Multimedia Keyboard: xkb_model: "evdev"
(**) Option "xkb_layout" "us"
(**) LITEON Technology USB Multimedia Keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse

The correct keyboard seems to be "Logitech USB Receiver", I don't understand why xorg find 3 keyboards ...



mon xorg.conf:
> Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice "Logitech USB Receiver"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
Option "XkbLayout" "fr"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbVariant" "latin9"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Logitech USB Receiver"
    Driver         "kbd"
Option "Device" "/dev/input/event4"
Option "XkbLayout" "fr"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbVariant" "latin9"
EndSection

I have added a device named "Logitech USB Receiver" but it doesn't work :/

---

