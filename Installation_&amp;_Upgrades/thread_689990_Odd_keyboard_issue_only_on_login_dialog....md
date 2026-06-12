---
title: "Odd keyboard issue only on login dialog..."
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by sonnychee on 2008-02-07
Hey Guys,

I downloaded a copy of Ubuntu Gutsy Gibbon for vmplayer.  The OS works fine but when I attempt to login with a new user account that I created I noticed that some of my keys map to different characters.  The letter y maps to z, and question mark (?) maps to underscore (_).  

When I do successfully login and open up a terminal window, the keyboard mappings are correct... any idea what settings I need to modify to correct the keyboard mappings on the login dialog?

Incidentally, I checked the keyboard layout and it is currently set to US-English.

Not a deal-breaker but I would hate to have to choose usernames/passwords to only use characters that I know are correctly mapped.

Sonny.

---

### Post by Partyboi2 on 2008-02-07
You could check your /etc/X11/xorg.conf  file to make sure that the keyboard is set to "us"
eg
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    [COLOR=Red]Option        "XkbLayout"    "us"


[/COLOR]

---

### Post by sonnychee on 2008-02-07
That worked!  Thanks Partyboi2.

Sonny.

---

