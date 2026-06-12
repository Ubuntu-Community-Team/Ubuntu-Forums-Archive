---
title: "X didn't start"
date: 2008-07-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by BwackNinja on 2008-07-27
It tells me (in an ironically blue screen) that an error occurred. So I looked in the log (attatched). After this, I couldn't write to my disk at all, with it complaining about a read-only filesystem. I went back into my hardy install, and nothing seems to be wrong with the permissions of my intrepid. I had also tried using startx. I will reboot again to see if it still occurs.

```
...
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
(II) RADEON(0): Damage tracking initialized for page flipping
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Found color CRT connected to primary DAC
in RADEONProbeOutputModes
(II) RADEON(0): Adding Screen mode: 1360x768
(II) RADEON(0): Adding Screen mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 2
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Found color CRT connected to primary DAC
in RADEONProbeOutputModes
(II) RADEON(0): Adding Screen mode: 1360x768
(II) RADEON(0): Adding Screen mode: 1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 2
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) UnloadModule: "mouse"
(II) UnloadModule: "kbd"

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x79) [0x80c2619]
1: [0xb7f7f400]
2: /usr/lib/xorg/modules/input//wacom_drv.so [0xb798a0fc]
3: /usr/X11R6/bin/X(DeleteInputDeviceRequest+0x52) [0x80d9f62]
4: /usr/X11R6/bin/X(CloseDownDevices+0x4b) [0x8084fbb]
5: /usr/X11R6/bin/X(main+0x4b0) [0x8071960]
6: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7b8a685]
7: /usr/X11R6/bin/X(FontFileCompleteXLFD+0x23d) [0x8070d11]

Fatal server error:
Caught signal 11.  Server aborting

```

And now it works like a charm... confusing

---

### Post by jpeddicord on 2008-07-27
It was probably just a hiccup on boot when the drives were mounted. It's possible that fsck tried to check the disk causing it to mount in read-only mode, but there are a lot of possibilities.

---

