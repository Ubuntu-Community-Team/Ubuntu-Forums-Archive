---
title: "How do I Temporarily Disable Notifications"
date: 2009-03-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Pat L.I. on 2009-03-13
Hello, I would like to temporarily Disable Notifications in my current session in order to test a game (fallout1) Im trying to run in an old version of Wine. (0.9.15)

Can someone point me in the right direction to temporarily turn off notifications from the command line. If I do this will they run again if I restart my session(logout,Log-in) or reboot the computer?

just for good measure can you also mention how to re-enable them, in case something goes wrong!!!
thank you

---

### Post by Pat L.I. on 2009-03-16
can anyone help with this?

---

### Post by DouglasAWh on 2009-03-25
I just want to turn them off forever...at least the ones from Pidgin.  Any help?

---

### Post by gwenn on 2009-03-26
Pidgin--Tools-- Plugins --LIBbla bla notify

---

### Post by DouglasAWh on 2009-03-26
> **gwenn said:**
> Pidgin--Tools-- Plugins --LIBbla bla notify

Thank God! I had looked everywhere except in the Plugins!

EDIT: is there not a way to thank people through the system anymore?

---

### Post by RonaldMcDollars on 2009-03-26
gwenn, thank you so much!!

---

### Post by andrewabc on 2009-03-26
> **DouglasAWh said:**
> EDIT: is there not a way to thank people through the system anymore?

Not currently. Those types of extras were causing problems with server/forum (my guess more overhead).
Read the sticky in offtopic board. (I think)

---

### Post by Denis_Cheremisov on 2009-03-26
> I just want to turn them off forever...at least the ones from Pidgin. Any help?
Lol, this is vista effect. Few people find vista beautiful, but most people find it horrible at work. I think it's because of its unbalanced and too garish theme. These notification are the same - they are eyecandy when full gamma and brigh, but they are horrible to use, and they looks ugly with not full bright/gamma.

---

### Post by t.rei on 2009-04-09
Those notifications are really disturbing in wine. 

So does anyone have the answer to the original question?

---

### Post by olskar on 2009-04-09
Would *killall notify-osd* in a terminal work or it just restarts after killing it?

---

### Post by kansasnoob on 2009-04-09
Well there's this:

[http://martinpitt.wordpress.com/2009/02/23/the-stracciatella-gnome-session/](http://martinpitt.wordpress.com/2009/02/23/the-stracciatella-gnome-session/)

Erick Brunzell's (that's me) post there also points to how you can re-enable the toolbar notifications for upgrades, restart, etc.

If you have Ctrl > Alt > Backspace activated you can change sessions doing that rather than rebooting.

To activate Ctrl > Alt > Backspace I like to edit /etc/X11/xorg.conf by adding the following lines (in bold):

> Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

[B]Section "ServerFlags"
        Option          "DontZap" "false"[/B]
EndSection 

---

