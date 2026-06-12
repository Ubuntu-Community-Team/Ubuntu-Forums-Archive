---
title: "gparted, paritioning ?'s"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by adam_n on 2010-01-12
I read a couple places that you're supposed to disable journaling before you resize partitions, and then enable it again afterward. Unfortunately, I read that after i started resizing. How exactly does disabling journaling help? Is it really necessary before paritioning? 
I'm using mac 10.6, hfs+.

---

### Post by raymondh on 2010-01-12
> **adam_n said:**
> I read a couple places that you're supposed to disable journaling before you resize partitions, and then enable it again afterward. Unfortunately, I read that after i started resizing. How exactly does disabling journaling help? Is it really necessary before paritioning? 
I'm using mac 10.6, hfs+.

To disable journaling in MAC

-  open disk utility > select the volumn > press OPTION > disable journaling.  To enable later on, same process.

Journaling, among others, is a continuous recording of the disc.  If you lose power or something, it allows you to return the system to a  good, reliable state. 

If this were windows, it is 'sort-of-like' a system restore for the disc.  If you remember/know windows, when you shutdown suddenly or unexpectedly, you will have to go through a checkdsk before a restart.  In Mac's, the journaling allows you to reboot to a good-state.

Is it needed (disabling and then enabling ? .... Maybe so especially when altering/resizing the HD using a partitioning editor. You may want to consult the a[pple sub-forum]("http://ubuntuforums.org/forumdisplay.php?f=328") here for a more clarified experience.  On my MAC, I turned it off prior to resizing.  On my netbook that has OSX, I just kept it on as I did not care if it borked (which it didn't).  Just remember to enable it afterwards.  Note ... you may see [errors after turning it on]("http://support.apple.com/kb/TS2028?viewlocale=en_US").

Good luck.  As always, have a working/tested back-up of your files.

Raymond

---

