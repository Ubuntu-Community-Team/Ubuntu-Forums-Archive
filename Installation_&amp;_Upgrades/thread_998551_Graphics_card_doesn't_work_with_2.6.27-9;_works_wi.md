---
title: "Graphics card doesn't work with 2.6.27-9; works with 2.6.27-7"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by rujith on 2008-11-30
I upgraded to 2.6.27-9-generic, and now, when I log out, the display
just goes blank.  I downgraded back to 2.6.27-7-generic, and it works
fine again.  I think there are some problems with the graphics card I
have, the Integrated Intel GMA X4500HD graphics card, in a Dell Studio
Desktop, but it used to work, so it's rather distressing that it
doesn't work with the new kernel release.  Any idea on what might have
caused it to stop working?
- Rujith.

---

### Post by hardyn on 2008-11-30
do you have the accompanying restricted modules for that kernel version?

---

### Post by falcon61102 on 2008-11-30
As hardyn mentioned, each time you update your kernal, you need to update the restricted modules for some of your drivers.  
It may be as simple as going to System>Administration>Hardware Drivers and enabling the restricted drivers through there, or you may have to re-install a new set.

---

### Post by rujith on 2008-12-01
> **falcon61102 said:**
> ... It may be as simple as going to
System>Administration>Hardware Drivers and enabling the restricted
drivers through there, or you may have to re-install a new
set.

"Hardware Drivers" shows no proprietary drivers on my system.  I
originally installed Ibex 8.10 and the graphics card just worked.
Only when I recently upgraded the kernel to 2.6.27-9 did the problem
occur.  Even then, on 2.6.27-9, I can boot, login, and do all the
usual stuff just fine.  It's just when I log out, and the screen gets
ready to show the login window again, does the display just go blank.
I have to do a hard reboot to recover.  I downgraded the kernel to
2.6.27-7, and everything works fine again.  So I figure that something
changed in the kernel that tickles the graphics card (Intel GMA
X4500HD).

- Rujith.

---

### Post by falcon61102 on 2008-12-01
Maybe the update got corrupted somehow.  Seems odd it would work at other times and not at shut down.  You could try the update again, or wait a couple weeks for the next kernal update and see if that one fixes it.

Also, check your system log with:
```
dmesg
```
to see if that contains any errors on shutdown.  It may be that the kernal has unloaded the graphics driver so your screen goes blank but something else is causing it to hang.

---

### Post by rujith on 2008-12-03
> **falcon61102 said:**
> Also, check your system log with dmesg to see if that contains any errors on shutdown.

Thanks, I'll try that.  Also I'll try the next kernel update.

I realized that the problem does occasionally occur as well with the old
kernel, maybe once in ten times.  It just seems to occur every time
with the new kernel.  I think there must be some random problem with the
graphics card under Linux that gets tickled under the right circumstances.

---

