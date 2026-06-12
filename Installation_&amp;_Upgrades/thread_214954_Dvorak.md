---
title: "Dvorak ?"
date: 2006-07-13
forum: Installation &amp; Upgrades
---

### Post by lordhedgehog on 2006-07-13
I installed Ubuntu with a standard keyboard layout, and I'd like to allow it to hot-switch back and forth with Dvorak.  I can't find the option anywhere...  Please tell me there's a way other than creating my own keyboard map!

---

### Post by lordhedgehog on 2006-07-14
Oops -- I meant I installed Xubuntu...  I know there's a Settings->Keyboard option in Gnome that does this, but I can't get Dvorak at all in Xubuntu.

---

### Post by theconley on 2006-07-22
Also looking for same feature in Kubuntu.

---

### Post by lordhedgehog on 2006-07-22
I eventually gave up and added it to the xorg.conf.  THe keybaord switcher tool just showed US, so it was useless.  So I ended up editing the Swedish  keyboard to match the US dvorak, and re-edited the xorg.conf to switch between US and Swedish.  A really stupid hack for what ought to be a basic option, in my opinion.  It still boggles my mind that there's no way to do that without mucking with foreign keyboard layouts.

In Kubuntu, open up System Settings and choose Regional and Accessibility.  Then choose Keyboard Layouts.  Add a second US keyboard, then select it.  The "Varient" drop-down box is now available, and you can switch it to Dvorak.  Switching options will allow you to automate switching between them.

BUT -- your flags are still hosed.  Here's what I did:

Edit /etc/X11/xkb/rules/xorg  -- someone smarter can probably tell you exactly which line to edit, but I replaced every instance of us(dvorak) with se(dvorak), and also %l(dvorak) with se(dvorak).  Probably only one needs changed, but I wouldn't know which.

Edit /etc/X11/xkb/symbols/se -- Replace the dvorak section with this:

// Swedish Dvorak
partial alphanumeric_keys
xkb_symbols "dvorak" {

    name[Group1]="Sweden - Dvorak";

    // Alphanumeric section

    key <TLDE> { [       grave, asciitilde, dead_grave, dead_tilde      ] };

    key <AE01> { [          1,  exclam          ]       };
    key <AE02> { [          2,  at              ]       };
    key <AE03> { [          3,  numbersign      ]       };
    key <AE04> { [          4,  dollar          ]       };
    key <AE05> { [          5,  percent         ]       };
    key <AE06> { [          6,  asciicircum, dead_circumflex, dead_circumflex ] };
    key <AE07> { [          7,  ampersand       ]       };
    key <AE08> { [          8,  asterisk        ]       };
    key <AE09> { [          9,  parenleft,  dead_grave] };
    key <AE10> { [          0,  parenright      ]       };
    key <AE11> { [ bracketleft, braceleft       ]       };
    key <AE12> { [ bracketright, braceright,  dead_tilde] };

    key <AD01> { [  apostrophe, quotedbl, dead_acute, dead_diaeresis    ] };
    key <AD02> { [      comma,  less,   dead_cedilla, dead_caron        ] };
    key <AD03> { [      period, greater, dead_abovedot, periodcentered  ] };
    key <AD04> { [          p,  P               ]       };
    key <AD05> { [          y,  Y               ]       };
    key <AD06> { [          f,  F               ]       };
    key <AD07> { [          g,  G               ]       };
    key <AD08> { [          c,  C               ]       };
    key <AD09> { [          r,  R               ]       };
    key <AD10> { [          l,  L               ]       };
    key <AD11> { [      slash,  question        ]       };
    key <AD12> { [      equal,  plus            ]       };

    key <AC01> { [          a,  A               ]       };
    key <AC02> { [          o,  O               ]       };
    key <AC03> { [          e,  E               ]       };
    key <AC04> { [          u,  U               ]       };
    key <AC05> { [          i,  I               ]       };
    key <AC06> { [          d,  D               ]       };
    key <AC07> { [          h,  H               ]       };
    key <AC08> { [          t,  T               ]       };
    key <AC09> { [          n,  N               ]       };
    key <AC10> { [          s,  S               ]       };
    key <AC11> { [      minus,  underscore      ]       };

    key <AB01> { [   semicolon, colon, dead_ogonek, dead_doubleacute ] };
    key <AB02> { [          q,  Q               ]       };
    key <AB03> { [          j,  J               ]       };
    key <AB04> { [          k,  K               ]       };
    key <AB05> { [          x,  X               ]       };
    key <AB06> { [          b,  B               ]       };
    key <AB07> { [          m,  M               ]       };
    key <AB08> { [          w,  W               ]       };
    key <AB09> { [          v,  V               ]       };
    key <AB10> { [          z,  Z               ]       };


};


Now edit /etx/X11/xorg.conf -- edit your keyboard section to look like this:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us,dvorak"
        Option "XkbOptions" "grp:shift_toggle"
EndSection


You will now have a US and a Dvorak keyboard configured (xorg.conf), but your Dvorak keyboard will be considered a Swedish keyboard (rules/xorg), but the layout will be identical to a US Dvorak (symbols/se).  So if you now enable the panel switcher, it will show a Swedish flag instead of a US flag while in Dvorak mode.  

Feel free to use any flag you want. :)

---

### Post by theconley on 2006-07-22
I was being stupid, I found it in KDE under something similar to System Settings->Regional Settings->Keyboard.

~Conley

---

