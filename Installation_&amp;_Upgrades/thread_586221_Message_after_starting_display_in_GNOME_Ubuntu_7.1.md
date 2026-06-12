---
title: "Message after starting display in GNOME Ubuntu 7.10"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by mep on 2007-10-22
Hello,

I get this message every time I log in as a user on system  Root user does not get this message

"  In a message box"

X System Keyboard settings differ from current Gnome Desktop.

Expected to see pc100 us where it show pc105 us

Then either lets me use X - pc105 or Gnome pc100

??  Where do I change ??  Other than that from 7.04 to 7.10 a dream... :)

---

### Post by andrei048 on 2007-10-22
I have the same problem, and it all started afeter I disabled for my user the xgl-server, adding ~/.config/xserver-xgl/disable. Now everytime Gnome starts, I get the same question about the keyboard, although in the xorg.conf and Sysyem->Preferences->Keyboard the settings look the same to me.

---

### Post by Wobedraggled on 2007-10-22
Edit this section of /etc/X11/xorg.conf

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
       ** Option          "XkbModel"      "pc105"**
        Option          "XkbLayout"     "us"
EndSection

Or go to System/prefrences/keyboard and change it there.

If they don't match you'll get the message.

---

### Post by mep on 2007-10-22
Thanks for the info.  I got the messsage to disappear.  One thing,  I too began getting this error after installing xgl-server and then actually uninstalling it.

Thanks for help...

---

