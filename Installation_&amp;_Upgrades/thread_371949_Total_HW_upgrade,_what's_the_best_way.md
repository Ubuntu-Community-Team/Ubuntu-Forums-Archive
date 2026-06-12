---
title: "Total HW upgrade, what's the best way?"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by arnethormodsen on 2007-02-27
I want to migrate my existing (Dapper) Ubuntu installation from an old 1 GhxPII system to a new 3.0 Ghz Pentium D system (I tried it on a toy system and I liked it enough to move on to a real computer ;-).  Totally different HW in every respect, an ASUS P5WD2 mobo if that matters.

Does it make more sense to just take the discs out of the old system and plug them into the new one, then dink around with the config until it works, or to do a complete new install of Ubuntu then add all the modules I've put onto the base?  My home dir is on a separate disc, so I've got no problems here.  It's the OS I'm wondering about.

If the second option is better, should I move on to Edgy?

If the first route is best, is there some way to get my current system to kick out a script or something what would allow me to automatically install all of the extra modules on top of a fresh intallation of Ubuntu?  If not, does anyone know the easiest way to go about this?

Finally, I need to get the SMP kernel too, obviously.  Any tricks to this or do I just install it?

Well, there's a book's worth of questions...

Thanks much,

--arne

---

### Post by bulldog on 2007-02-27
The easiest way is a reinstall,the most learning experience would be to reconfigure your existing install :) 

Just try to move your hard disk in the new computer and boot into recovery mode.
Then you can try this command to see if you can get it working again.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This can resove problems you encounter,but it's a little depending on how much there is changed in your new computer.

I should give it a try, though,you can always come back here to ask for a little help.

---

