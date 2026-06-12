---
title: "Keyboard error: a though question"
date: 2005-03-15
forum: Installation &amp; Upgrades
---

### Post by ceti on 2005-03-15
Since I've upgraded from warty to hoary, my [QUESTION MARK/SLASH] key is dead.
My keyboard lay-out & keyboard model is Brazilian ABNT2
Is it a bug (question mark).
I can't make questions anymore, which is sooooooo frustrating.
Any ideas or tips (question mark; ok, this is ridiculous...)

Thanks
ceti

---

### Post by Musashi on 2005-04-16
sudo gedit /usr/X11R6/lib/X11/xkb/keycodes/xfree86

Scroll to the very end of file
// For brazilian ABNT2 keyboard. by Ricardo Y. Igarashi(iga@that.com.br)
xkb_keycodes "abnt2" {
    include "xfree86(basic)"
    <BKSL> = 94;
    <AC12> = 51;
    <KPPT> = 134;
};

and include a option:

    <AB11> = 211;

Will look like:
// For brazilian ABNT2 keyboard. by Ricardo Y. Igarashi(iga@that.com.br)
xkb_keycodes "abnt2" {
    include "xfree86(basic)"
    <BKSL> = 94;
    <AB11> = 211;
    <AC12> = 51;
    <KPPT> = 134;
};

then 

$sudo dpkg-reconfigure console-data

Select from arch list
qwerty
brazilian
standart

reset the X
on gnome question about the keyboard layout choose x window configuration!

Then it's done!

---

### Post by ceti on 2005-04-17
thanks, it worked perfectly.

cheers
ceti

---

