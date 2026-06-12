---
title: "Upgrade completed by Ubuntu won't start"
date: 2014-08-14
forum: Installation &amp; Upgrades
---

### Post by asearle on 2014-08-14
Hi Everyone,

Yesterday I tried to upgrade from 12.04 to 14.04:  The upgrade seemed to run through, finishing and requesting a reboot, which I did.  The system booted and the "Ubuntu" logo came up (with the flashing dots) but that is all I got :-(

I booted with the shift key pressed and go various boot options including safe mode and three previous Linux releases.  I tried a number of these but got exactly the same (i.e. never past the Ubuntu Logo).  

This has never happened to me before as previously I have always been able to get Ubuntu to boot.

Any thoughts?  Or should I give up and reformat the disk?

Many thanks for any tips that you can give me.

Yours,
Alan Searle
Cologne, Germany

---

### Post by Bashing-om on 2014-08-14
asearle; Hi !

Not much to go with - yet.
Try to boot to a text terminal:
at the grub menu press the 'e' key for edit mode -> boot parameters screen;
Arrow down and across to the terms "quiet splash" and replace them withe the term "text" with out the quotes. Key combo ctl+x to continue the boot process.
Do you now boot to terminal (TTY1) ?
Can you log in here ( enter username and password - no response to the screen here; enter password blindly )?

If so we can look at what might not be taking place;
Else, we do something else.

[INDENT][INDENT]it's ubuntu
[INDENT][INDENT][INDENT][INDENT]it's fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by asearle on 2015-01-07
I reformatted in the end.  But I'm sure that, if I had had the time, it could have been fixed:  Ubuntu/Linux is pretty much rock-solid.

---

### Post by Bashing-om on 2015-01-07
asearle; Hey;

The important thing is that you are up and running -
That Nuclear solution always works !

[INDENT][INDENT]we will have fun
[INDENT][INDENT][INDENT]playing other games
[INDENT][INDENT][INDENT][INDENT]some other time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

