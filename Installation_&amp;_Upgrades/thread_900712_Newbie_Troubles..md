---
title: "Newbie Troubles."
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by funky_claude on 2008-08-25
Hello,

  I'm new to Ubuntu, and Linux in general, and have been having some difficulties installing it on one of my machines, so of course I have a few newbie questions that I couldn't find answers for in the documentation section of the site or older forum posts.  I'm used to Windows, so I thought I'd load Ubuntu on one of the extra machines that I have lying around to have a look at it.

  I'm trying to do a fresh install with Ubuntu 8.04 (LTS), but I'm used to doing it the somewhat outdated 'Windows' way, what with deleting partitions and such.  My machine currently has no OS installed and no partitions.  When I boot the machine up off of the Ubuntu disk, I choose the 'Install Ubuntu' option, it starts up, which takes a few minutes, but then it goes to what looks like an empty desktop screen.  On the empty desktop screen I have a cursor but no icons or anything and the only thing I'm able to do there is move the cursor around.  What exactly am I doing wrong here that I'm just not seeing?

---

### Post by spiderbatdad on 2008-08-25
Not sure what to make of that. You should see a cd icon, labeled "install." And you would click that icon to proceed with the installation. You should also see a top and bottom panel, showing menus, etc.
It seems like the cd image is corrupted. Did you check it for defects from the startup screen?

---

### Post by OutOfReach on 2008-08-25
Hmm how much memory do you have on the machine you're trying to install on?

---

### Post by funky_claude on 2008-08-25
> **spiderbatdad said:**
> Did you check it for defects from the startup screen?

Yes, I did that first thing after burning the disk and the test came out fine.

---

### Post by funky_claude on 2008-08-25
> **OutOfReach said:**
> Hmm how much memory do you have on the machine you're trying to install on?

Currently, I have a 256MB stick of SDRAM in there and also a 128MB stick.

---

### Post by coffeecat on 2008-08-25
The desktop hasn't completely loaded. Have a look at [this webpage]("https://help.ubuntu.com/community/GraphicalInstall") (second screenshot) to see what the desktop should look like, although with the Hardy Heron version the wallpaper shows a - um - heron.

Try pressing ctrl-alt-Backspace. This will kill the GUI and take you to a login screen. Just wait for it to log in automatically and the desktop just *might* load properly second time around.

---

### Post by ugm6hr on 2008-08-25
What hardware are you using (i.e. RAM, processor)?

Ubuntu now recommends 384+MB RAM to install from LiveCD.

Sounds like you are using the Install Ubuntu option, which does not boot a full desktop (i.e. no panels, menu etc), but should auto-start the installation Wizard.

Common reason for this not to happen is insufficient RAM.

EDIT: I see you have about enough RAM.  Is this shared with a graphics card (which may reduce the available RAM)?

Try the first boot option to try Ubuntu without Installing.

---

### Post by OutOfReach on 2008-08-25
Yes it seems that your lack of memory is preventing the desktop from loading quickly, it probably will load...eventually.

---

### Post by funky_claude on 2008-08-25
> **ugm6hr said:**
> What hardware are you using (i.e. RAM, processor)?

Ubuntu now recommends 384+MB RAM to install from LiveCD.

Common reason for this not to happen is insufficient RAM.

Is this shared with a graphics card (which may reduce the available RAM)?

Try the first boot option to try Ubuntu without Installing.

The processor is an AMD Athlon 1.2ghz, and yes, it's on-board video.  I agree that it could be a memory issue.  Now that I've tried doing a 'Ctrl+Alt+Backspace' as suggested above, my cursor has become very laggy.  I'll try slapping in another 256MB stick of memory in a few minutes and see if that fixes it.

---

