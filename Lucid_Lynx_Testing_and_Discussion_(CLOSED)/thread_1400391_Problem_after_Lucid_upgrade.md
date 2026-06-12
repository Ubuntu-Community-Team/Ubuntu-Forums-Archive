---
title: "Problem after Lucid upgrade"
date: 2010-02-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dawynn on 2010-02-06
OK -- having trouble trying to figure out what's going on here.

I put together a text-only installation from an old disk.  Everything was working nicely through the Karmic upgrade.  Then I upgraded to Lucid.  I was able to reboot fine at the Karmic stage, but the Lucid stage won't boot very well.

It locks if I try to use the Lucid kernel at all.  A boot from the Karmic kernel into recovery mode will let me at least get to a command line.  But continuing into a normal boot will lock me up, just as requesting a normal boot at Grub will cause similar issues.

I'm running an Athlon Classic 1.2Ghz.  Any ideas where I should start looking?

---

### Post by dawynn on 2010-02-11
NM.  Stripping out Plymouth seems to have worked for me.  I was able to get to a command line, even with the new kernel.  In fact, I was able to install lxde, lxdm, and xorg and get to a gui screen.

---

