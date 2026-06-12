---
title: "update manager doesn't check for updates automatically"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ogcub on 2009-10-15
I have updated my system from jaunty to karmic and ever since i have to check for updates manually because update manager doesn't notify me of any available updates. Anybody has similar Problems?

---

### Post by DougieFresh4U on 2009-10-15
> **ogcub said:**
> I have updated my system from jaunty to karmic and ever since i have to check for updates manually because update manager doesn't notify me of any available updates. Anybody has similar Problems?

I may be wrong, but I thought it was changed to only notify like once a week or some thing.

---

### Post by philinux on 2009-10-15
> **ogcub said:**
> I have updated my system from jaunty to karmic and ever since i have to check for updates manually because update manager doesn't notify me of any available updates. Anybody has similar Problems?

If you want the old behaviour back you have to untick the auto-launch box.

---

### Post by edujose on 2009-10-15
Hi philinux, which config program did you use? (screenshot did not capture app's title bar, where app name resides).

Looks like some graphical gconf frontend, but I'm a complete noob regarding gconf.

---

### Post by VMC on 2009-10-15
> **edujose said:**
> Hi philinux, which config program did you use? (screenshot did not capture app's title bar, where app name resides).

Looks like some graphical gconf frontend, but I'm a complete noob regarding gconf.

Look at bottom. Where it says screen shot-Configuration Editor.

---

### Post by ogcub on 2009-10-15
> **philinux said:**
> If you want the old behaviour back you have to untick the auto-launch box.
thanks, I'll try hovever i doubt this is the issue, because package information doesn't get updated automatically. Every day i get package information was updated X days ago, and have to force check manually.

---

### Post by gdonwallace on 2009-10-15
The problem could be that Karmic is still in beta.  I do the same thing, but attributed it to Karmic not being an actual release yet.  Maybe that will change with the RC or the final release when that comes out.

---

### Post by edujose on 2009-10-15
Thanks VMC, I searched that text in Synaptics and found "gconf-editor" in the results (it's indeed the program used by philinux).

About update-manager not showing updated package information when opened, it seems to be an issue since Jaunty (9.04). See e.g. [bug 356152]("https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/356152") (update-manager doesn't show updates, even after 1 week).

---

### Post by rajeev1204 on 2009-10-15
> **philinux said:**
> If you want the old behaviour back you have to untick the auto-launch box.

Can you cofirm this ? I have tried this a million times and 6 months later, i still havent seen an icon.Sure, when i update manually i see an icon but what good is that.

I have been updating manually since 9.04.

---

### Post by Amaranth on 2009-10-15
There is a bug open about the apt cron job not actually running apt-get update anymore.

[https://launchpad.net/bugs/449535](https://launchpad.net/bugs/449535)

Should be fixed soon though.

---

