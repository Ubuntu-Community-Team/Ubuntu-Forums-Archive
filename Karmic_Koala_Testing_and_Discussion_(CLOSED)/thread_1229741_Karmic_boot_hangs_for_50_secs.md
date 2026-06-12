---
title: "Karmic boot hangs for 50 secs"
date: 2009-08-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by daetsy on 2009-08-02
As title. Boots to about 15% then hangs for about 50 secs before completing boot sequence.

---

### Post by Seventh Reign on 2009-08-02
Are you going by the size of the loading bar for the 15%?  If so then I'm having the same problem.

After I finish a few CD Burns I think I'll reboot with quiet splash off and see what it says.

---

### Post by Yofel on 2009-08-02
Easiest way to check what's causing the hang is by using 'bootchart'. Install it and bootchart-java, reboot, and you'll find a log and a .png of the boot in /var/log/bootchart/.

If you're interested, there is a whole lot of them in [this]("http://ubuntuforums.org/showthread.php?t=1229111") thread.

---

### Post by Seventh Reign on 2009-08-02
> **Yofel said:**
> Easiest way to check what's causing the hang is by using 'bootchart'. Install it and bootchart-java, reboot, and you'll find a log and a .png of the boot in /var/log/bootchart/.

If you're interested, there is a whole lot of them in [this]("http://ubuntuforums.org/showthread.php?t=1229111") thread.


Just as I suspected .. I broke one of the pins for the power cable on my floppy drive a few days ago.  Deleted Quiet Spash from grub.cfg.  It was giving me an fd0 in/out error.  Disabled the Floppy from the Bios and it booted up in no time.

Installed Bootchart too.. gonna post my log in the other post.

---

### Post by daetsy on 2009-08-02
I don't have a floppy, so I disabled it in the BIOS and I now get an uninterrupted boot. Now boots in 17s. It never happened in Jaunty, so must be a new feature(?) of Karmic. Thanks guys.

---

### Post by MacUntu on 2009-08-02
Check it out: [https://bugs.launchpad.net/linux/+bug/384579](https://bugs.launchpad.net/linux/+bug/384579)

---

### Post by wayne_cat on 2009-08-02
> **MacUntu said:**
> Check it out: [https://bugs.launchpad.net/linux/+bug/384579](https://bugs.launchpad.net/linux/+bug/384579)

this bug is still not solved :shock:

---

### Post by daetsy on 2009-08-02
> **MacUntu said:**
> Check it out: [https://bugs.launchpad.net/linux/+bug/384579](https://bugs.launchpad.net/linux/+bug/384579)

Yep. That's the feller. Thanks for the pointer. I'm glad I don't use a floppy, it seems to be a bigger problem for those who do!

---

