---
title: "[SOLVED] I can only do partial upgrades (64 bit)"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by phenest on 2008-10-14
I dunno if this is just me, but I've only been able to do partial upgrades for the last few days.
```
The following packages have been kept back:
  gstreamer0.10-plugins-good icedtea-gcjwebplugin linux-generic
  linux-headers-generic linux-image-generic linux-restricted-modules-generic
  openjdk-6-jre swfdec-mozilla

```

---

### Post by phenest on 2008-10-14
Ok, using Synaptic worked, but apt-get and Update-Manager would only do partial upgrades. A bug? I'll still mark as solved though.

---

### Post by heavensblade23 on 2008-10-14
I had that issue too.

---

### Post by linomac on 2008-10-14
use only at CLI
aptitude update
aptitude full-upgrade
nothing better than this for dependency solutions
it even proposes u solutions

---

### Post by fictivetoast on 2008-10-14
Ditto here on 64-bit.  The same listed packages (icedtea, gstreamer's good plugins, etc) have actually been kept back for about a week for me - I'd assumed it was a normal development hiccup, only just got around to bothering to see what the deal was.  Turning to aptitude on the CLI took care of it, as suggested.  Strange though that synaptic and the update manager were so stumped though.

---

### Post by jblackhall on 2008-10-15
Someone correct me if I'm wrong, but I think this package is being replaced (needs to be removed and a new package is used instead):
icedtea-gcjwebplugin

The problem is Update Manager can't remove packages, so you're prompted for a Partial Upgrade (which can remove packages).  Partial Upgrading can be a bit of a hazard, but as long as you pay attention to what you're doing, you should be ok.  The main thing you want to **be sure of** is that only icedtea-gcjwebplugin is going to be removed.  You can either do Partial Upgrade from Update Manager or you can go into Synaptic, reload your package list and click "Mark All Upgrades".  Again, just double-check that the only thing set to be removed is "icedtea-gcjwebplugin" before you start the upgrade.  There should be another java plugin being installed in its place.  If you see multiple packages being removed, you should wait and try again later (until you only see the one listed to be removed).

---

