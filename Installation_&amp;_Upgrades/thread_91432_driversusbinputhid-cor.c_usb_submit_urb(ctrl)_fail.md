---
title: "drivers/usb/input/hid-cor.c: usb_submit_urb(ctrl) failed"
date: 2005-11-17
forum: Installation &amp; Upgrades
---

### Post by Ubuntist on 2005-11-17
Every time I boot Ubuntu, the message[INDENT]
drivers/usb/input/hid-cor.c: usb_submit_urb(ctrl) failed
[/INDENT]
appears on the screen early in the boot process.

If searched the system with find, and there is no file called hid-cor.c.

Ubuntu seems to work fine, but is this something I should worry about?  If so, how might I fix it?

---

### Post by ranf on 2005-11-17
[QUOTE=Ubuntist]Every time I boot Ubuntu, the message[INDENT]
drivers/usb/input/hid-cor.c: usb_submit_urb(ctrl) failed
[/INDENT]
appears on the screen early in the boot process.

If searched the system with find, and there is no file called hid-cor.c.
[/QUOTE]
That should read **hid-core.c**. You would find it if you had the linux-source package installed.

Do you have any problems with an USB mouse or USB keyboard?

---

### Post by Ubuntist on 2005-11-18
> **ranf]
That should read **hid-core.c**. You would find it if you had the linux-source package installed.
[/QUOTE]
Thank you very much.  It's definitely **hid-cor.c**, without the 'e' that it complains about, but /usr/src/linux-source-2.6.12/drivers/usb/input/hid-core.c **does** exist.  So my guess is that the error message is being truncated somewhere along the way.  The specific error message appears in exactly once in hid-core.c:
```

        if (usb_submit_urb(hid->urbctrl, GFP_ATOMIC)) {
                err("usb_submit_urb(ctrl) failed") said:**
> 
Do you have any problems with an USB mouse or USB keyboard?

The mouse and keyboard seem to work fine, but I suspect that neither is USB, because neither plugs into a USB slot on the PC.  Also, the invoice describes the mouse as a "PS/2 w Button Wheel Mouse" -- I presume it would mention "USB" if the mouse were USB.  So the error probably isn't so important for my system, but I'd still like to track it down if I can.

---

### Post by ranf on 2005-11-18
[QUOTE=Ubuntist]
The definition of usb_submit_urb is in /usr/src/linux-source-2.6.12/drivers/usb/core/urb.c, but unfortunately it is beyond my understanding.  Would you have a hint for a noob as to where to go from here?
[/QUOTE]
It is beyond mine as well 
[QUOTE=Ubuntist]The mouse and keyboard seem to work fine, but I suspect that neither is USB, because neither plugs into a USB slot on the PC.  Also, the invoice describes the mouse as a "PS/2 w Button Wheel Mouse" -- I presume it would mention "USB" if the mouse were USB.  So the error probably isn't so important for my system, but I'd still like to track it down if I can.[/QUOTE]
Maybe this message simply means "no USB core devices found"? I have no idea.
But I wouldn't worry too much as you don't have any USB core devices attached.

---

### Post by Ubuntist on 2005-11-20
Thanks very much, ranf.

---

