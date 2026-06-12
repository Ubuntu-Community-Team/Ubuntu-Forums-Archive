---
title: "Polish qwertz (pl2) keyboard layout on Xubuntu"
date: 2006-10-04
forum: Installation &amp; Upgrades
---

### Post by acidic68 on 2006-10-04
Just installed Xubuntu 6.06 on my old IBM. I cannot find anymore where to set my keyboard layout to the Polish qwertz layout (pl2). Can you tell me how to do it? That layout is used by fast typers and I can't imagine working on my computer using the default Polish layout that I find in Xubuntu.

Thanks.
-- 
acidic68

---

### Post by whizbaby on 2006-10-04
Since nobody has a better idea by now:
add pl2 in /etc/X11/xorg.conf at following position

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "**pl2**"
        Option          "XkbVariant"    "nodeadkeys"
EndSection

You can have several layouts you can switch e.g.

Option          "XkbLayout"     "pl2,us.pl"

Now restart the x-server (ctrl-alt-del) , login and add the *keyboard layout switcher* to the xfce panel (right mouse on panel and add item)

---

### Post by acidic68 on 2006-10-05
Thanks, for trying to help, but this didn't work. The layout is not recognized I presume, since my layout switcher shows 'UNKNOWN'. I read somewhere that breezy doesn't come with pl2, whatever that means. Is there no way to add it, even if it's not included in the system?

---

### Post by smyru on 2006-10-05
As far as I remember no changes are needed, since in Ubuntu both Polish drivers programmer's and classic quertz one are combined into one. One has to switch between them with the system tools. 

I remember doing that for a friend I converted to Ubuntu. But that was in the vanilla Ubuntu, and you are runnung Xubuntu, thus I have no answer.

---

### Post by acidic68 on 2006-10-06
Thank you both for replying, your posts got me thinking. I searched a bit the man pages, compared xorg.conf from my other linux machine (where I do not use the Polish keyboard layout though) and came up with the solution.

Here is what I edited in my /etc/X11/xorg.conf:

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "pl,fi"
Option "XkbVariant" "qwertz,"
Option "XkbOptions "grp:ctrl_shift_toggle"
EndSection

I use two keyboard layouts, between which I switch with ctrl+shift (XkbOptions). The Polish qwertz layout (in Polish klawiatura maszynistki) is specified with the XkbVariant option. After the comma one can specify a variant for the Finnish keyboard, if needed. I did not set any.

Restart x-server with ctrl+alt+backspace.

---

