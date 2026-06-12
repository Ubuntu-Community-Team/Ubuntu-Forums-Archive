---
title: "[SOLVED] Still having problems with keyboard..."
date: 2008-10-02
forum: Installation &amp; Upgrades
---

### Post by kwboom on 2008-10-02
HI there..... I am still having some problems with my keyboard typing the wrong keys.....    like when I hit my backslash, question mark I get   é and É.  When I try to use one of the arrows above the comma or the period I get ''''''' above the comma and ......... above the period.  (and yes I was holding the shift, and the shift works for everything else)

Thanx for the replies in advance......

---

### Post by wpshooter on 2008-10-02
Did you try another keyboard ?

---

### Post by knattlhuber on 2008-10-02
Did you try to change the keyboard layout (System > Preferences > Keyboard > Layout tab)?

---

### Post by Bucky Ball on 2008-10-02
All depending what layout you are after the best way to fix this is in your xorg.conf file. Before you do this, if you have any customisations in there or just for practise, it is an idea to back the file up:

**sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.backup**

Open it by pasting this in a terminal:

**sudo nano /etc/X11/xorg.conf**

In the keyboard section:

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        **Option          "XkbLayout"     "us"**
EndSection
```

... manually change the line I have in bold. Where I have "us", change to the country layout you are after. You may find some other options in there that are screwing you up also. 

Tell us how you get on ... :)

---

### Post by kwboom on 2008-10-03
Well thankyou for all the help again.... got it fixed...... was set for canada for some reason and that messed it all up, changed back to US and all is good......

---

### Post by miegiel on 2008-10-07
Thanks Bucky Ball, I was having problems with my ' and " keys. I had to hit space after the keys to get them or I'd get chars like ... uhm ... can't make them anymore ](*,) ... like an e with " on top of it. really annoying.

System > Preferences > Keyboard > Layout fixed the problem till the next reboot. The weird thing was that I didn't need to change the settings there. I only needed to add any layout (I used albanian because it was on top) and remove the layout I added. Just to repeat the routine after the next bootup.

Adding 2 #'s in /etc/X11/xorg.conf fixed it \\:D/
Thanks for pointing me in the right direction.


```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
#	Option		"XkbVariant"	"alt-intl"
#	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection
```

---

