---
title: "problems setting dvorak layout up."
date: 2005-02-08
forum: Installation &amp; Upgrades
---

### Post by graigsmith on 2005-02-08
ok. i just installed.  i picked dvorak layout during install.  and when it booted up. the keyboard layout was in qwerty.  i was able to figure out how to get dvorak in gnome desktop.

but for some reason, whenever i try to log in. the keyboard layout is in qwerty.  

i want to be able to log in using dvorak.

---

### Post by Phil Devor on 2005-04-21
Yes... I, too want to log in with the superior keyboard layout...

...does anyone know how to do this?

---

### Post by nautilus on 2005-04-21
tada, here i am to save your days!

for terminal, copy the dv keymap to your default, like so:

```
cp /usr/share/keymaps/i386/dvorak/dvorak.kmap.gz /etc/console/boottime.kmap.gz
```

there are a few dvorak variants in there, too.

for X, edit /etc/X11R6/xorg.conf and find the keyboard section ("Generic Keyboard") and add/edit the XkbLayout to be "dvorak"

all done, if it worked; enjoy :D

although, i think mine worked from installation, so, hmm weird :/

i hate getting stuck in "',.pyf" too ;)

---

### Post by Phil Devor on 2005-04-21
nautilus:  you rock

...works perfectly...

Thanks!

---

