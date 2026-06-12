---
title: "GRUB_DEFAULT=saved not working after 9.10 -&gt; 10.04 upgrade (grub 1.98)"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by stegemangreg on 2010-05-21
Is the "saved" option for grub2 not available after the new upgrade?

I had grub2 setup to let me load either windows or ubuntu, whichever I last used, and it worked.  After the last update to Ubuntu I cannot get this to work anymore.  I can successfully change the default boot entry by entering a number, e.g. "GRUB_DEFAULT=3" but when I put in "GRUB_DEFAULT=saved" it always defaults to the first entry, the latest Ubuntu.  I can also change the screen resolution for the grub menu on this computer, but on another computer I cannot change the screen resolution for grub or restore the 'saved' option (I have not tried to change the boot default by numbers on this other computer though).  

I am only editing /etc/default/grub and running update-grub, is there another script or file I should be changing as well since the update?

Thank you

---

### Post by Navario on 2010-05-22
I had the same problem but adding GRUB_SAVEDEFAULT=true in /etc/default/grub as suggested in this thread [http://ubuntuforums.org/showthread.php?t=1417361&highlight=GRUB_DEFAULT%3Dsaved](http://ubuntuforums.org/showthread.php?t=1417361&highlight=GRUB_DEFAULT%3Dsaved) did solve it.

---

