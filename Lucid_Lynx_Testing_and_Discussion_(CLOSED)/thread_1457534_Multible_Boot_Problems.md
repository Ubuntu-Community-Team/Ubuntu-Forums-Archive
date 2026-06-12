---
title: "Multible Boot Problems"
date: 2010-04-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Bobhuber on 2010-04-18
I really don't even know where to start on reporting a bug or bugs on this.
Upgrade from 9.10 to Lucid on a AMD 64 X2 Nvidia graphics 3/gig with 500 gig HD ext4.
1. Boot failure - Grub showing 2 kernels available,attempted to boot from the first one with multiple Plymouth boot errors. Eventually booted from the second Grub listing (2.6.31.20) and discovered that the first Kernel (2.6.32.21) even though shown in the grub menu had never been installed. Loaded the Kernel and headers thru Synaptic,update grub and was able to boot.
2. After booting into the desktop- Incorrect video drivers. Remove (whatever was loaded I have no clue) and reinstall the correct driver (good sign at least it let me this time). Set up Compiz and all is well I think.
3. Reboot machine - Incorrect video drivers or drivers not installed, no Compiz with an X for the mouse curser. System>Preferences>Appearance select Extra desktop effects and it reloaded the drivers. Setup Compiz again.Afraid to reboot now so I'll continue this post.
4.Lightning not compatible with Thunderbird Mail.
Gonna reboot now and see what happens. One other comment.When its working this system is FAST. Slow boot but noticeable improvement on an already fast computer.

---

### Post by ranch hand on 2010-04-18
Don't use Lightning (or know what it is), don't like compiz but it worked last time (a month) I checked so I really know nothing about those problems.

Your first problem was obviously caused by a faulty upgrade.  Not too uncommon at this stage of development but somewhat troubling.

If you upgraded this time you probably did last time.  If that is the case you may still be on ext3.

If you are, I would strongly suggest backing up your data and going with a clean install.  The RC should be out the 22nd sometime.

---

### Post by Bobhuber on 2010-04-18
> **ranch hand said:**
> Don't use Lightning (or know what it is), don't like compiz but it worked last time (a month) I checked so I really know nothing about those problems.

Your first problem was obviously caused by a faulty upgrade.  Not too uncommon at this stage of development but somewhat troubling.

If you upgraded this time you probably did last time.  If that is the case you may still be on ext3.

If you are, I would strongly suggest backing up your data and going with a clean install.  The RC should be out the 22nd sometime.
I'm using ext4 with multiple drives and a good backup of 9.10 . I've tried loading the Beta (1&2)both with an upgrade and a fresh install. I see several bug reports with similar problems for the kernel not loading or incorrect grub menu and a bunch on the Nvidia drivers. It loses the desktop settings on every reboot. I'll fool with it a bit more.

---

