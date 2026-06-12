---
title: "blocked updates in Jaunty?"
date: 2009-04-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cptrohn on 2009-04-03
Just curious about these, I have never had this issue before...

I only have 3, and I think that 2 of them are for clam and the other has something to do with KDE4.2 (even though I'm not exactly sure what it is)

Does it just block things that don't apply to your system?

---

### Post by cariboo on 2009-04-03
The updates are not installed if there are dependencies missing, give it a couple of days for the dependencies to catch up.

Jim

---

### Post by rajeev1204 on 2009-04-03
I have ekiga which seems to be blocked.

I cant select it for install.

---

### Post by zika on 2009-04-03
> **rajeev1204 said:**
> I have ekiga which seems to be blocked.
I cant select it for install.
force update of ekiga in synaptic allowing removal of old libraries and installation of new (replacements) it works ...

---

### Post by andrewabc on 2009-04-03
ekiga has been present for past 1.5 weeks but does not install.

I just noticed that xorg won't install now, says it cannot be found on server. So maybe that update got pulled?

---

### Post by novafluxx on 2009-04-03
Are you doing apt-get dist-upgrade or just apt-get upgrade?

---

### Post by andrewabc on 2009-04-03
> **novafluxx said:**
> Are you doing apt-get dist-upgrade or just apt-get upgrade?

I'm just using update manager.
I tried synaptic "mark all upgrades" but it still didn't download ekiga.

No idea about my xorg download failure since I only noticed it this afternoon.

---

### Post by FuturePilot on 2009-04-03
> **andrewabc said:**
> I'm just using update manager.
I tried synaptic "mark all upgrades" but it still didn't download ekiga.

No idea about my xorg download failure since I only noticed it this afternoon.

Search for ekiga and then manually mark it for upgrade. That's what I had to do.

---

### Post by andrewabc on 2009-04-03
> **FuturePilot said:**
> Search for ekiga and then manually mark it for upgrade. That's what I had to do.

Thanks that worked perfectly.

---

### Post by IanW on 2009-04-04
This happened because some of the packages ekiga depends on were replaced by packages with different names, which conflicted with the installed packages for the old version.

These old dependencies had to be uninstalled before ekiga could be marked for upgrade by update manager.

---

