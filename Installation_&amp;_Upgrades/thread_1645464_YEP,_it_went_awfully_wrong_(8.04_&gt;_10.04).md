---
title: "YEP, it went awfully wrong (8.04 &gt; 10.04)"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by Wim Sturkenboom on 2010-12-14
grumble grumble, moan moan

Did an online upgrade today from 8.04 to 10.04 and it went awfully wrong; the upgrade was done with errors (snmpd and snmptrapfmt) and I was warned that I possibly would end up with an unusable system; and indeed, system now falls back to busybox during boot, does not see the boot directory with *ls* but grub starts and shows the old *menu.lst* (I should probably not have confirmed to keep the existing menu.lst)

8.04 was an upgrade from 6.06

Backups were made of the home directories of the three main users; currently creating some extra backups of HD dedicated to photos as well as windows data partition to an external HD (the backups of those are scattered all over the house; stupid me). So no damage done there.
For the other occasional users (they have not used the system for at least three months) it's tough luck if they did not create backups.

Most important question:
I've created backups from within evolution. I assume that those are compatible with a possible newer version of evolution (using restore. Correct ?

Second question:
What's the best way to go? Just do a clean install and do not format the home partition? Any compatibility issues to be expected with newer versions of applications and older config files?
Or just do a clean install including formatting of the home partition and get it over and done with?

PS
The bad thing: consumed a big part of my bandwidth cap and wasted 8 hours.
The good thing: it could have been worse if I had to go looking for backups. Lesson learned; know where they are.

---

### Post by akand074 on 2010-12-14
Honestly, if your coming all the way from 6.06 upgraded to 8.04 then upgraded to 10.04, I would personally do a fully clean install. Then a few years from now at 12.04, you can do the same. A clean install every 2 years seems reasonable.

---

### Post by Quackers on 2010-12-14
Some of the settings in your /home folder may not be compatible with later versions.

---

### Post by Wim Sturkenboom on 2010-12-14
OK, clean install

Thanks people

---

