---
title: "No display after upgrade to 9.10 (ATI Radeon)"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by john_roshi on 2010-01-23
Dear Ubuntu fans,

I upgraded my HP Elitebook 6930p from 9.04 to 9.10.
When X starts the display shows random lines.
I can boot into "recover" mode from GRUB and get the command prompt.
9.04 worked fine so I'm pretty sure it's not the video card.
The video card is ATI Radeon HD 3400.

Has anyone else seen this problem? 
Is there a workaround or fix I can issue from the command line?

Thanks,
--john

---

### Post by Fir3chi3f on 2010-01-23
Did you upgrade to 9.10 from the Update manager? or did you burn a disk and install 9.10 over 9.04?

If you did use update manager to upgrade, did you install proprietary Ati drivers in 9.04? 

If you had, Ubuntu might still be trying to use those drivers, which do not work in 9.10 of Xorg I believe. 

Within the recovery console, try running a good old

```
sudo apt-get update
sudo apt-get upgrade
```

That should upgrade fglrx if you installed it from the repositories.
Good luck and post back

---

### Post by john_roshi on 2010-01-24
> **Fir3chi3f said:**
> Did you upgrade to 9.10 from the Update manager? or did you burn a disk and install 9.10 over 9.04?

I upgraded using Update Manager.
> **Fir3chi3f said:**
> 
If you did use update manager to upgrade, did you install proprietary Ati drivers in 9.04? 
If you had, Ubuntu might still be trying to use those drivers, which do not work in 9.10 of Xorg I believe. 

I don't think so.  I don't remember doing so.  And when I used Preferences>Display, I got the default dialog, not some vendor-specific one.


> **Fir3chi3f said:**
> 
Within the recovery console, try running a good old

```
sudo apt-get update
sudo apt-get upgrade
```

That should upgrade fglrx if you installed it from the repositories.
Good luck and post back

I tried your suggested update/upgrade but I didn't see anything in the console that looked like it did anything, and the problem persists.

Would installing ATI driver help?  How do I do that from the command line? Is it a matter of using apt-get with the appropriate package name?

---

### Post by john_roshi on 2010-01-24
Also, the machine boots from the 9.10 Live CD with no problem and goes to the graphical desktop fine. 

So somehow Upgrade Manager messed things up.

--john

---

### Post by john_roshi on 2010-01-26
I gave up.   For whatever reason, Upgrade Manager messed me up beyond repair.  I had to reinstall from a LiveCD.  Much reinstalling of applications ensued.  :-(

But now the display is working again.

---

