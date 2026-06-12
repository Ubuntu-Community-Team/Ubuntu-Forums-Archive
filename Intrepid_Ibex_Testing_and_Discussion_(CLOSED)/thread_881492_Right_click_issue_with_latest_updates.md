---
title: "Right click issue with latest updates"
date: 2008-08-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by berbs on 2008-08-06
I run intrepid on a macbook pro. Since the last update, the right click is now triggered by using the down arrow key (very annoying) instead of the right alt key. Any help would be greatly appreciated. 

I also noticed the returned of the infamous "Error activating XKB configuration." message #10499906.

Here is what I have

```

/etc/X11/xorg.conf

Section "InputDevice"
    Identifier      "Generic Keyboard"
    Driver          "kbd"
    Option          "XkbRules"          "xorg"
    Option          "XkbOptions"        "lv3:ralt_switch"
EndSection

```

In the keyboard preference panel, the keyboard is Macbook Pro. The accessibility settings are set and the 3rd level chooser is set to the right alt key, as it should.

Any help would be greatly appreciated.


-- partial solution --

I used the xev utility and realized that the keycode for the right click changed from 116 to 134 (116 is now the down arrow, why?!?). I changed the settings in .xmodmap from

keycode **116** = Pointer_Button3
keycode 108 = ISO_Level3_Shift

to 

keycode **134** = Pointer_Button3
keycode 108 = ISO_Level3_Shift

The right alt key now works and so does the down arrow. Not sure why the settings changed though.

---

