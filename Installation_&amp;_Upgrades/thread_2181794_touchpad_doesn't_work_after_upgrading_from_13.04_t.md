---
title: "touchpad doesn't work after upgrading from 13.04 to 13.10"
date: 2013-10-19
forum: Installation &amp; Upgrades
---

### Post by danicotani on 2013-10-19
[COLOR=#000000]Dear members,[/COLOR]

[COLOR=#000000]I upgraded from 13.04 into 13.10.[/COLOR]
[COLOR=#000000]The touchpad on my laptop doesn't work since the upgrade.[/COLOR]
[COLOR=#000000]Connecting an external USB mouse works fine.[/COLOR]
[COLOR=#000000]I've tried to define settings for touchpad on system settings--->mouse & touchpad, but this is not possible.[/COLOR]

[COLOR=#000000]Do you have a solution?[/COLOR]

[COLOR=#000000]Thanks[/COLOR]
[COLOR=#000000]Dani[/COLOR]:confused:

---

### Post by rihikz on 2013-10-19
That is not enough information to solve your problem. What laptop is it? Have you done anything that might have caused this? Did the upgrade went fine with no errors?

---

### Post by danicotani on 2013-10-19
I've just solved it.
The default definitions had to be changed.
Thanks

---

### Post by sebastian-perezteres on 2013-10-28
> **danicotani said:**
> I've just solved it.
The default definitions had to be changed.
Thanks

Hi man, can you explain what you did to fix it please? I'm having the same issue.
Its a Toshiba E45t-A4200
For what I can tell it has an elantech v8 touchpad
In 13.04 worked just like a simple mouse, no multi-touch, after upgrading to 13.10 it doesn't work at all.

xinput list shows:
    PS/2 Elantech Touchpad        id=12

xinput --test 12 Doesn't show any output at all

---

### Post by vitriolix on 2013-11-06
This is happening to me on my Sony Vaio S15 as well.  If I login with Gnome 3 it works fine, but with Unity no trackpad.

---

### Post by vitriolix on 2013-11-07
strange.  this happens if i "switch users" and login as another user on this machine.  it's like the old user session has a lock on the mouse.  If I run this it can grab the mouse for the new session, but switching back to the first session again has no mouse:

sudo modprobe -r psmouse ; sudo modprobe psmouse

---

