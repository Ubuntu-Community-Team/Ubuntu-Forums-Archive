---
title: "Some questions about Karmic"
date: 2009-10-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by CheeseEatingBulldog on 2009-10-28
Right, I have tested a stick with 9.10 and have a few questions:

Grub 2
How do I get a menu to show the list of kernels, and not just show "grub 2" for a split second and load os?

Terminals
How do enable ctrl + alt + F1-F12 to get to a prompt once gdm has loaded (very annoying with testing that one can't drop to prompt)?

GDM
How do I enable crtl + alt + backspace to reload GDM, you know like it always did (very annoying testing resolutions/drivers for cards that this has been disabled).

Thanks in advance.

---

### Post by Giblet5 on 2009-10-28
The full grub2 menu is the default.

Ctrl-Alt-F1 is enabled on an install and it worked on my Live image.

You can enable exiting Xorg via Ctrl-Alt-Backspace in Jaunty and Karmic using [this link]("http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html").

---

### Post by CheeseEatingBulldog on 2009-10-28
Right, so maybe I only saw minimal grub2 due it booting from a usb stick. Ok sounds fair.

The quick drop to terminal didn't work for me, but could also be due to usb boot.

Thanks for the link, but does this also work in Karmic, seeing as link is for jaunty?

Cheers for that btw.

---

### Post by shadow120 on 2009-10-28
to bring up the grub menu hold shift when grub starts

---

### Post by Giblet5 on 2009-10-28
> **CheeseEatingBulldog said:**
> Right, so maybe I only saw minimal grub2 due it booting from a usb stick. Ok sounds fair.

The quick drop to terminal didn't work for me, but could also be due to usb boot.

Thanks for the link, but does this also work in Karmic, seeing as link is for jaunty?

Cheers for that btw.


Yep. System -> Preferences -> Keyboard

Click the Layouts tab, Click the Layout Options... button, expand the "Key sequence to kill the X server" item, put a checkmark beside Ctrl-Alt-Backspace.

All done.

---

