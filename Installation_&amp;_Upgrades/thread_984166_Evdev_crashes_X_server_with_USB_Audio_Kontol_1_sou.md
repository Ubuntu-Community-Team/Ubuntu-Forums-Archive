---
title: "Evdev crashes X server with USB Audio Kontol 1 sound card"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by harvixen on 2008-11-16
Hi all,

after upgrade from 8.04 to 8.10 my external USB audio card Audio Kontrol 1 by Native Instruments crashes severly X-server thanks to the bug in evdev driver and..who knows what else? What exactly happens is when AK 1 is plugged in works, but when I touch any of its buttons they are understood as key input event and the whole X is reset or killed..

Audio Kontrol 1 gets recognized by X-server (never happened before): 

(II) config/hal: Adding input device Audio Kontrol 1
(**) Audio Kontrol 1: always reports core events
(**) Audio Kontrol 1: Device: "/dev/input/event11"
(II) Audio Kontrol 1: Found keys
(II) Audio Kontrol 1: Configuring as keyboard
(II) XINPUT: Adding extended input device "Audio Kontrol 1" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Audio Kontrol 1: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Audio Kontrol 1: xkb_model: "pc105"
(**) Option "xkb_layout" "de"
(**) Audio Kontrol 1: xkb_layout: "de"

..and then happily crashes X:

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x79) [0x80c3009]
1: [0xb8009400]
2: /usr/bin/X(xf86PostMotionEvent+0x68) [0x80daa48]
3: /usr/lib/xorg/modules/input//evdev_drv.so [0xa27bbfca]
4: /usr/bin/X [0x80c3207]
5: /usr/bin/X [0x80b2d7c]
6: [0xb8009400]
7: /usr/bin/X(Dispatch+0x7e) [0x808c5ce]
8: /usr/bin/X(main+0x47d) [0x8071d1d]
9: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7bfb685]
10: /usr/bin/X [0x8071101]
Saw signal 11.  Server aborting.

So here it is. I upgraded Alsa from .17 to .18a version, evdev is also fresh from the repos.

Does anyone have any clue or a temporary fix, mybe permanent solution? ;)


so far: 

[https://bugs.launchpad.net/ubuntu/+bug/301892/](https://bugs.launchpad.net/ubuntu/+bug/301892/)

---

### Post by ralfcoenen on 2009-01-22
I'm struggling with the same problem. Until now searching for a solution doesn't bring a workaround.

If you found a hint or maybe a workaround please give us a message.


All the Best

Ralf

---

### Post by ralfcoenen on 2009-01-23
I've found an interesting side 

[http://wiki.ubuntuusers.de/HAL/Eingabeger%C3%A4te?highlight=hal%20eingabegerat](http://wiki.ubuntuusers.de/HAL/Eingabeger%C3%A4te?highlight=hal%20eingabegerat)

I think that the audio Kontrol1 is treated like a keyboard because there is no definition of the device in one of the .fdi-files in /usr/share/hal/fdi/policies.

---

