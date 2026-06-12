---
title: "Eee PC 901 tochpad (Elantech) configuration"
date: 2009-09-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by HankB on 2009-09-30
I have partially configured my touchpad using gpointing-device-settings and System -> Preferences -> Mouse, but I remain unable to fully configure it as it works under Jaunty.

what works:
 - 2 finger scrolling
 - LMB click and click/drag
 - RMB click (lower right corner)

what doesn't work:
 - MMB click (upper right corner.)

I think I use tpconfig on Jaunty (have to reboot to confirm) but that seems to no longer work. I can only run it as root due to perms on /dev/psaux and it seems not to have the desired effect:
```
hbarta@bonsai:~$ sudo tpconfig -3
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
2 button mode; corner tap is right button click.
hbarta@bonsai:~$ 
``` (This command shhould set it to three button mode.)

Is there some option to get the upper right corner tap recognized as the middle mouse button?

thanks,
hank

---

### Post by synthaxx on 2009-10-02
How have you renabled it? Because in Jaunty it just worked out of the box.

I'm still searching for a way to get it back to the jaunty way of actually working, can't live without two fingered scroll anymore.

/EDIT:  workaround in: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/346645](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/346645) worked.

---

### Post by HankB on 2009-10-02
> **synthaxx said:**
> ... can't live without two fingered scroll anymore.
I just edited my post to fix the typo in the title and add "and System -> Preferences -> Mouse."

Between that setting dialog and gpointing-device-settings I have two fingered scrolling and left and right mouse button tapping working. I would still like to get the middle mouse click back.

-hank

---

### Post by cororok on 2009-10-03
I'm using eeepc 1000h with ubuntu9.10 including xubuntu-desktop.

At the xubuntu-desktop two finger scrolling works out of box and two finger click works as a while button click but it works as a right button at ubuntu.

---

