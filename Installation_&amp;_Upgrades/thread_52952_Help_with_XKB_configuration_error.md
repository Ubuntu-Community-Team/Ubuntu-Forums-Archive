---
title: "Help with XKB configuration error"
date: 2005-07-29
forum: Installation &amp; Upgrades
---

### Post by vdorta on 2005-07-29
I installed and like Ubuntu but I still have a problem setting up a us_intl keyboard with deadkeys, which I require to write Spanish and French words. Gnome doesn't have it and the closest one is " us with deadkeys," which I selected. This Gnome keyboard preference worked in Firefox and Thunderbird, but not in OpenOffice. I am new to Gnome and this was strange to me because I know the KDE keyboard setting is a global one.

As a good newbie, I couldn't leave well enough alone and I then tried to modify the xorg.conf file. The remedy not only didn't work but got me into deeper trouble. Everything seems to work except that now I can't even write accents in Firefox or Thunderbird; on top of that I get this error screen at X startup:

"Error activating XKB configuration"

I followed the bug instructions and the following is what I get.

*xprop -root | grep XKB* shows:

XKB_Rules_Names backup (string) = xorg, pc104, us, ,
XKB_Rules_Names (string) = xorg, pc104, us, ,

*gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd* shows:

layouts = [us]
model = [pc 105]
overrideSettings = true
options = []

I can see the problem but have no idea how to fix it. Both Gnome and xorg.conf have " pc104"  keyboard selected.

Thanks.

---

### Post by Skatox on 2005-08-02
> **vdorta]I installed and like Ubuntu but I still have a problem setting up a us_intl keyboard with deadkeys, which I require to write Spanish and French words. Gnome doesn't have it and the closest one is " us with deadkeys," which I selected. This Gnome keyboard preference worked in Firefox and Thunderbird, but not in OpenOffice. I am new to Gnome and this was strange to me because I know the KDE keyboard setting is a global one.

As a good newbie, I couldn't leave well enough alone and I then tried to modify the xorg.conf file. The remedy not only didn't work but got me into deeper trouble. Everything seems to work except that now I can't even write accents in Firefox or Thunderbird said:**
> 
model = [pc 105]
overrideSettings = true
options = []

I can see the problem but have no idea how to fix it. Both Gnome and xorg.conf have " pc104"  keyboard selected.

Thanks.
 Have you tryed to change your keyboard language from the gnome-keyboard-properties?? choose your key language.

---

### Post by Xterminator on 2005-08-02
```
layouts = [us_intl]
model = [pc104]
overrideSettings = true
options = [us_intl]
```

in xorg.conf 

```
Option "XkbModel" "pc104"
Option "XkbLayout" "us_intl" 
```

The Keymap **us_intl** is  **US English w/ Deadkeys**

---

