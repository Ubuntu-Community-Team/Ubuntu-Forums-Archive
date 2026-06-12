---
title: "Fresh 16.10 Install - Invisible Cursor"
date: 2016-10-25
forum: Installation &amp; Upgrades
---

### Post by porkchop_001 on 2016-10-25
Hi guys. The title says it all. I just installed a fresh copy of 16.10 onto my PC. I've spent the last 3 hours looking for fixes online, sadly to no avail :(

I've run ```
xsetpointer -l | grep Pointer
``` and can clearly see my connected USB mouse.

I've run ```
gsettings set org.gnome.settings-daemon.plugins.cursor active false
``` and it does nothing.

I've run ```
sudo apt-get install gdm
``` to switch form lightgdm to normal gdm. Still no luck.

Any hints?

---

### Post by slickymaster on 2016-10-25
*Thread moved to **Installation & Upgrades**.*

---

### Post by Freddi67 on 2016-10-26
Common issue on a computer with touchpad & touchscreen on 16.04 ("stable"), but the issue gets no attention on Launchpad. I believe the cursor is just not being rendered (by Xorg?). Still I consider reliability of the cursor an essential quality criterium.


[LIST]
[*]if the cursor is missing at first login after boot, I logout and login again and the cursor appears
[*]if it happens temporarily, it may reappear after switching to tty1 and back (ctrl+alt+f1; ctrl+alt+f7)
[*]if you enable "gnome-tweak-tool &#8594; mouse &#8594; Show location of pointer", you can poll the mouse location with ctrl
[/LIST]

---

### Post by porkchop_001 on 2016-10-27
Thanks for the input guys. I eventually snapped and tried an alternative USB creator to UNetbootin called Rufus (which Ubuntu actually recommend in the first place according to this [https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)) and once I booted it up the mouse was fine. Quite odd. All sorted though :)

---

### Post by Geoffrey_Arndt on 2016-10-27
So, just to be clear . . you did a reinstall with a new usb bootable flash-stick created using Rufus, . . . or were/are you running off a Live usb flash-stick and not the internal drive(s)?

---

