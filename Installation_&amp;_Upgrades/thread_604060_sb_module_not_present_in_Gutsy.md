---
title: "sb module not present in Gutsy?"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by abovett on 2007-11-05
I've just upgraded an old Compaq Armada 7400 laptop to Gutsy and the sound no longer works. It has (I believe) an ESS1879 sound chip. I previously had it working using the sb module but this does not appear to be present in Gutsy. Is this true? Has support for it been discontinued with this kernel? Can anyone suggest an alternative?

Thanks

Andy

---

### Post by aldo.mateos on 2008-02-17
Hi. You should install linux-backports-modules-generic.

---

### Post by BCW142 on 2008-02-17
I have basically the same problem and thus could use the same answer, I have an standard SB16 card installed. Under W2K is shows as IRQ 10, DMAs 1,7 normal 220H port.
It took me a few minutes to figure out what you meant so that's no answer for a Newbie. First thing is to install Ubuntu on a drive, then Under Applications, Accessories, pick Terminal. In the Terminal window that comes up type:
sudo apt-get install linux-backports-modules-generic
You are likely to have setup a password that it will ask you for before installing.
Hopefully that is enough information to get you started.:)

---

### Post by abovett on 2008-02-18
> **aldo.mateos said:**
> Hi. You should install linux-backports-modules-generic.

Thanks. I'll give that a try next time I have the machine out. I'm curious - how would or should I have discovered that's where it was?

---

