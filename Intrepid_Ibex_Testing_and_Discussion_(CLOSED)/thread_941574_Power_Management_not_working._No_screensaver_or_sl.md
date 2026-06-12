---
title: "Power Management not working. No screensaver or sleep. Anyone else got this?"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by philinux on 2008-10-08
I'd like to know if anyone else got this.

---

### Post by perlluver on 2008-10-08
Well, my screensaver works after I turned off a setting in Compiz, but after yesterdays updates, even though my screen is set not to turn off, it does anyway.  I hope it was fixed in today's updates.  The setting I turned off is unredirect fullscreen windows.

---

### Post by philinux on 2008-10-08
I've not got compiz running so it's not that. I remember the screensaver did work a while back. But not now.

---

### Post by dabl on 2008-10-08
Kubuntu's power manager and screensaving functions seem to be working.  I used kpowersave's suspend to RAM last night and it came back up OK, and the screen saver shuts off my CRT after 15 minutes, just as I have set it.

---

### Post by philinux on 2008-10-08
Ok progress as such. Changed appearance visual effects to non. Now screesaver works and the machine goes to sleep.

Upon wake everything is borked. Have to REISUB reboot.

---

### Post by BARlotta on 2008-10-12
I am seeing problems with this as well (I am running amd64 version).

I have screensaver set to come on in 20 minutes (it does not).

Display should shutoff in 40 minutes (it does not).

I do notice a small flicker where it appears that the screensaver is going to come on (screen goes to black) but then it immediately comes back to the desktop.

I am using compiz as well.  I just unchecked the "unredirect fullscreen windows" to see if that has any effect or not.

---

### Post by philinux on 2008-10-12
Ah. glad it's not just me then.

---

### Post by aethralis on 2008-10-12
Could it be this bug?

[https://bugs.launchpad.net/ubuntu/intrepid/+source/compiz/+bug/278112](https://bugs.launchpad.net/ubuntu/intrepid/+source/compiz/+bug/278112)

---

### Post by ktp on 2008-10-12
You are not alone...I just noticed this today...screensaver did not came on when it should have.

---

### Post by BARlotta on 2008-10-12
I just ran a few tests with the "unredirect fullscreen window" in General Options of compiz and can confirm that this is "causing" the issue.  When I uncheck the option I get normal screensaver/power management features (screensaver comes on in 20 minutes and display shuts off in 40).

Since I don't run many fullscreen applications shutting it off is fine for me, although I did not have this issue with hardy.

---

### Post by BARlotta on 2008-10-12
> **aethralis said:**
> Could it be this bug?

[https://bugs.launchpad.net/ubuntu/intrepid/+source/compiz/+bug/278112](https://bugs.launchpad.net/ubuntu/intrepid/+source/compiz/+bug/278112)

Yes this is exactly the problem I am seeing.

---

### Post by philinux on 2008-10-12
> **BARlotta said:**
> I just ran a few tests with the "unredirect fullscreen window" in General Options of compiz and can confirm that this is "causing" the issue.  When I uncheck the option I get normal screensaver/power management features (screensaver comes on in 20 minutes and display shuts off in 40).

Since I don't run many fullscreen applications shutting it off is fine for me, although I did not have this issue with hardy.

Have you bugged this?

---

### Post by scaine on 2008-10-12
Just to confirm - the bug reported above by aethralis is an Intrepid Launchpad bug - so the developers are aware of it, philinux.  I can also confirm that unticking the "unredirect fullscreen window" option in Compiz Settings Manager, as the bug (and BARlotta) advises works a treat and fixes the screensaver problem.

---

### Post by philinux on 2008-10-13
> **scaine said:**
> Just to confirm - the bug reported above by aethralis is an Intrepid Launchpad bug - so the developers are aware of it, philinux.  I can also confirm that unticking the "unredirect fullscreen window" option in Compiz Settings Manager, as the bug (and BARlotta) advises works a treat and fixes the screensaver problem.

Yes this workaround does the job.

Also resume from sleep i.e. pressing power button works a treat with no loss of sound or other functionality.
I'm not marking this solved as the bug is still open.

---

