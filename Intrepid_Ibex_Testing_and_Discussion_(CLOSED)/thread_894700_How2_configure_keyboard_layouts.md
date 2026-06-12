---
title: "How2 configure keyboard layouts"
date: 2008-08-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by yotam on 2008-08-19
I am pasting here what I just filed in:
[https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/259489]("https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/259489")

Binary package hint: xkeyboard-config

Just installed Xubuntu/Intrepid 8.10-alpha4.
I am confused what is the 'right' way to configure the keyboard
to support both 'us' and 'il(lyx)' layouts.
In my good-old /etc/X11/xorg,conf I had:

    Section "InputDevice"
            Identifier "Generic Keyboard"
            Driver "kbd"
            Option "XkbRules" "xorg"
            Option "XkbModel" "pc105"
            Option "XkbLayout" "us,il"
            Option "XkbVariant" ",lyx"
            Option "XkbOptions" "grp:alt_shift_toggle,grp_led:scroll"
    EndSection

There are several conflicting tips/tools. I tried several combinations
of them and restarted X, hal, and the whole system.
But so far I did not manage to be able to switch between layouts.

+ Using this good old /etc/X11/xorg.conf.
  In Xubuntu:
    Settings-Manager -> Keyboard -> Layouts ->
    Check the 'Use X configuration' checkbox.

+ Using
    dpkg-reconfigure console-setup
  or editing /etc/default/console-setup

+ Supplying an XML file like:

    # cat /etc/hal/fdi/policy/x11-keyboard.fdi
    <?xml version="1.0" encoding="UTF-8"?>

    <deviceinfo version="0.2">
      <device>
 <match key="info.capabilities" contains="input.keyboard">
   <merge key="input.xkb.rules" type="string">xorg</merge>
   <merge key="input.xkb.layout" type="string">us,il(winkeys)</merge>
   <merge key="input.xkb.variant" type="string">,lyx(winkeys)</merge>
   <merge key="input.xkb.options" type="strlist">grp:alt_shift_toggle</merge>
   <append key="input.xkb.options" type="strlist">grp_led:scroll</append>
 </match>
      </device>
    </deviceinfo>

Cuurently I get:
    # setxkbmap -print
    xkb_keymap {
     xkb_keycodes { include "evdev+aliases(qwerty)" };
     xkb_types { include "complete" };
     xkb_compat { include "complete" };
     xkb_symbols { include "pc+us+inet(evdev)+il(lyx):2" };
     xkb_geometry { include "pc(pc104)" };
    };

But yet I did not yet figure out how to get to the alternative il(lyx) layout.

-- yotam

---

### Post by yotam on 2008-08-19
Adding in [FONT="Fixedsys"]/etc/X11/xorg.conf[/FONT]

```
Section "ServerFlags"
  Option "AllowEmptyInput" "True"
EndSection

```
solved the problem.

---

