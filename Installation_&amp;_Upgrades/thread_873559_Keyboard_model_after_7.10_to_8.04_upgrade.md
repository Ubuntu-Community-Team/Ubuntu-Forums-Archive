---
title: "Keyboard model after 7.10 to 8.04 upgrade"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by mlewies on 2008-07-29
Hi

I use an external pc-105 keyboard on my laptop which worked perfectly under Gutsy. However since upgrading to 8.04, using my numeric keypad now causes X to crash.

I have tried forcing the keyboard model to a generic pc-105 keyboard and ensuring it is in my xorg.conf:

---------------------
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection
----------------------

Does anyone know what could be causing this?

---

### Post by clanmackay on 2008-07-31
I have a Microsoft Natural Internet Keyboard.  In Gutsy it worked as it was supposed to: type numbers.  In Hardy, it does nothing.  Not sure if this is the same issue, but it sure sounds reasonable.

(Yes, smart aleck, I know about the Num Lock key.)

---

### Post by ddixonr on 2008-07-31
On my desktop running hardy, I constantly (everytime I reboot) have to go into keyboard settings and tell it not to use the keyboard to control the mouse. Unchecking the box immediately allows the numpad to work. I don't know why it won't remember to do this every time, but it just takes a second and I don't have to reboot very often.

---

### Post by clanmackay on 2008-07-31
> **ddixonr said:**
> On my desktop running hardy, I constantly (everytime I reboot) have to go into keyboard settings and tell it not to use the keyboard to control the mouse. Unchecking the box immediately allows the numpad to work. I don't know why it won't remember to do this every time, but it just takes a second and I don't have to reboot very often.

That did the trick.  Thank you.

---

