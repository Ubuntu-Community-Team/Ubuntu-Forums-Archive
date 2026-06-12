---
title: "Upgrade to 10.4 hung and now will not boot"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by solomonson on 2010-05-12
This morning I decided to upgrade from 9.10 to 10.4.  It downloaded all of the packages and started to install and about half way through, a popup box said something about not having network connectivity.  For some reason I lost networking on that system (my other computer had network).

At that point in the installation there was a progress bar that said "40 minutes remaining".  I closed the popup and hoped for the best.  After about an hour the progress bar did not move.  I opened top and saw a process called lucid.  It was eating about 40% CPU.  The hard drive light was not on.  I killed lucid and restarted the networking service.  It did not come up.  So I restarted the machine.  

Now I can't even get into Ubuntu.  It seems to hang at tmidity service.  I restarted in linux safe mode and I see a curses dialog to try restore but a bunch of errors overwrite the dialog and it doesn't seem to work.

Other possibly important details:
-Ubuntu was installed under Windows Vista
-Vista still boots fine 
-It's an AMD64 install on a laptop.

What can I do to get Ubuntu back?

---

### Post by dino99 on 2010-05-12
i think its better to make a clean install again

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by solomonson on 2010-05-12
Is there a way to access the data?  I had a few files I was hoping to keep.

---

### Post by Catharsis on 2010-05-12
You should get to them if you boot the LiveCD.

---

### Post by belwood on 2010-05-13
I did the same upgrade on my laptop his morning with the same result - appears to hang on boot.  :-(  

Unfortunately, both the live CD and install CD do the same thing - blank screen on boot, no disk activity; looks hung or dead.

My workaround was to boot from the HD in recovery mode (grub was still working fine).
- ran the package repair (just in case)
- booted to low-resolution.

Everything appears good (for now).  My problem was likely to do with my vid driver - it's an old Dell X300 laptop.

---

