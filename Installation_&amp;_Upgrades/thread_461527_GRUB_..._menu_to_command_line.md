---
title: "GRUB ... menu to command line"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by mijj on 2007-06-01
does anyone know how (or if it is possible) to go from the grub menu to teh grub commandline ?

why? 

recently, on the (unknown to me) kernel update, as a practical joke, ubuntu replaced my menu.lst with a new one with a completely fallacious UUID.  Thus .. Ubuntu would just hang after i selected an option on the grub menu.  (You wouldnt believe how long it took me, an utter novice, to sus  out the meaning of the UUID.)

Anyway .. i managed to see the contents of menu.lst from the paragon partition manager.  That alerted me to the fact that the menu.lst was changed.   Comparisons with my archived menu.lst showed that the UUIDs had changed.

So .. i found a version of grub that i could burn to disk and boot into and give command line instructions to start up Ubuntu bypassing the menu.lst (using path instead of UUID).

I anticipate more shenannigans of this type further down the line.   I'd like to be able to go from the grub menu to the grub command line without having to search for a long lost disk.

Does anyone know how?  It'd be really useful.
[I]
<makes coffee and waits patiently....>[/I]

---

### Post by confused57 on 2007-06-01
You can use the grub CLI:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by mijj on 2007-06-02
ah ...

what i mean is ...

when presented with the grub boot menu, is there a way to quit the menu and come out to the grub cli without having to select a menu option?

---

### Post by mijj on 2007-06-02
oops ...

[http://users.bigpond.net.au/hermanzone/p15.htm#cli]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")
> This is Grub's 'Command Line Interface', you get this by pressing your 'c' key from the GRUB menu.
You can return to the Grub menu by pressing your 'Esc' key. 

:oops:

I'm gonna add that to the grub menu so i dont forget.

Thanks for the link, confused57.

---

