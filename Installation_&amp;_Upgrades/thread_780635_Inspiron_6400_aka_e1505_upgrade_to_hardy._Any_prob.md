---
title: "Inspiron 6400 aka e1505 upgrade to hardy. Any problems ?"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by tomaasj on 2008-05-03
Previous 6.10 install and additional upgrades to Gutsy on mentioned laptop resulted in broken internet connection: no wireless.  Can I expect the same when upgrading to Hardy ?  Anyone had the guts to upgrade with similar hardware ?  

Just curious...  

Inspiron 6400 aka e1505

---

### Post by The Groovy Guru on 2008-05-04
I upgraded my 6400 with ATI X1400 which was previously upgraged from feisty. First I booted up on a live CD and backed up the system partition using partimage. The upgrade failed at the end, complaining about some package, gnome-games-data or something. I also forgot to remove the Envy installed fglrx drivers. 

I put the original system back, removed the gnome-games-data package and the fglrx drivers and then it worked. The only problem now is I can't get direct rendering to work.

---

### Post by The Groovy Guru on 2008-05-04
p.s. I now have direct rendering working. I put the latest ati driver downloaded directly from the ATI site on. I had no success with EnvyNG, but did keep the xorg.conf file it made.

---

### Post by tomaasj on 2008-05-04
since I am no linux-expert, maybe it is better not to upgrade but do a fresh install ?...

---

### Post by The Groovy Guru on 2008-05-04
You could do that. The upgrade should work though.
Just depends on how much stuff you need to custimize etc. 

If bandwidth is not an issue you could try the upgrade and if it doesn't go well do the fresh install.

I know how to fix the issues that popped up with my upgrade, so if you have any of those I can help you fix them. I am no expert though.

Anyway, good luck!

---

