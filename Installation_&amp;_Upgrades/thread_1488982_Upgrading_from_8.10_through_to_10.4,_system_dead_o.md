---
title: "Upgrading from 8.10 through to 10.4, system dead on 9.10"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by kemushi on 2010-05-20
So the option was made available through Update Manager to upgrade the OS version from 8.10 (Intrepid) to the next best 9.04, this install went well.  I next upgraded to 9.10 and was no longer able to open the OS.  Grub seems fine, at first it brought me to a login screen (seemingly different than before) for Ubuntu, I did login with my usual credentials but I only saw a black screen for a long duration.  Several tries reveal that it won't even load the login screen at all, it just does some minor processing with a blank screen.  I have tried this multiple times with no luck, and I cannot find any problems on forums or in docs that would come close to similar.  

I assume that I need a repair disk or some kind of option to recover the OS if the install went badly.  But I absolutely cannot reinstall as I have very important documents on the existing OS.  Stupidly I did not back them up.

Where should I start?  I have the alternate disk but there does not seem to be anything but a shell option for recovery and I honestly don't know the back end of linux very well at all for this kind of repair.  I really just want to see if the upgrade was never finished and possibly complete it or redo it again.

By the way, this is on a Dell Inspiron 600m laptop, so if it seems like maybe my hardware is too old for 9.10 or later please let me know.  Thanks!

---

### Post by davidmohammed on 2010-05-20
during booting try using the recover option and then find out what type of graphics you have

lspci | grep VGA

If you have nvidia or ATI graphics - follow the advice in the sticky thread above.

If you have intel graphics try booting with 
i915.modeset=1 or
i915.modeset=0

in your grub line (press e on grub display and add the above before ''quiet splash')

---

### Post by kemushi on 2010-05-20
This helped, it was in fact ATI.  I hadn't even noticed that sticky thread because I wasn't looking for video problems.  I ended up fresh installing 10.4 over my unused windows part and it is working nicely.  I was also about to recover my files from the old install.

---

