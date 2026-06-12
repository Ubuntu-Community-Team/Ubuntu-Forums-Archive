---
title: "How do I add two HDD's; one with XP the other with Ubuntu...."
date: 2010-12-23
forum: Installation &amp; Upgrades
---

### Post by Stormsy on 2010-12-23
Hey,

I am thinking of buying a larger HDD and installing Win XP onto it, but keeping my old, smaller HDD and install Ubuntu on it.  Thereby having two HDD with two different OS on them.

What I would like to know is how I got about doing this?  Would the following sequence of events satisfy;

1.) Remove the old, small HDD;
2.) Install the larger, newer HDD and format it;
3.) Install Win XP onto newer HDD;
4.) Add the old, small HDD and format it with Ubuntu?

Also - I do not want to have GURB2 load up at boot, but rather Windows Boot Manger instead (in GRUB I think it lists the Kernel Versions for Ubuntu when it updates, which can be confusing for the family to select - I'm trying to keep it simple for them ;) )

Any help would be great.  I am fine with replacing a HDD, but adding another and installing another OS onto it is confusing... :S
Thanks,
Stormsy.  :)

---

### Post by dandnsmith on 2010-12-23
It can get a bit messy for you if you want the Windows Boot Manager as the first thing seen.

Presumably the rest of the family would prefer Windows, so why not accept the Grub install, and just set the default OS to boot to be Windows, and use a fairly short timeout so they don't have to wait too long (but you can still get in to boot another system).

---

### Post by Stormsy on 2010-12-23
You have a point there.

When Ubuntu updates the Linux generic versions, they always appear in the GRUB boot loader, instead of deleting the previous one, and so you end up with a list of the different versions.  

How do you get rid of those versions so that you just have the latest on appear in the GRUB boot screen?

Thanks,
Stormsy.

---

