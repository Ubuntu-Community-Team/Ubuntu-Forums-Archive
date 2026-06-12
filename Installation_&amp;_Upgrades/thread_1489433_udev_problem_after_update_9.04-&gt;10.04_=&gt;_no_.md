---
title: "udev problem after update 9.04-&gt;10.04 =&gt; no mouse, no keyboard"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by Zebro on 2010-05-21
Hi all,

I face a very stupid problem and I guess it is related to most of the other problems posted here about mice and keyboards not working. However, I could not yet find any solution.

PROBLEM: After updating the Error message about low graphics mode (missing driver) appeared and I could not proceed because I could not click the ok button ... mouse didn't work ... and no keyboard. But at that point I just assumed this was because of the error message. So I reinstalled the driver by pointing the unintstall script to the right folder
```

export FORCE_ATI_UNISTALL=/usr/share/ati
```
Now the graphics works, but the mouse, touchpad and the keyboard do still not work. When I boot I reach the login screen but can not enter anything.

I found in the Xorg.0.log the following Errors:

(II) config/udev: Adding input device Power Button (FF) (/dev/event0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Video Bus (/dev/event6)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Lid Switch (/dev/event1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (CM) (/dev/event2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device UVC Camera (17ef:4807) (/dev/event
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/event5)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/event4)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/event9)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/event10)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/mouse3)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/event3)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/event7)
(II) No input driver/identifier specified (ignoring)

It seems to me that this is the key point in solving the issue. But I don't know how to proceed.

Any suggestings how this can be fixed?

Best regards,

Zebro

---

