---
title: "apt doesn't know that gutsy is available."
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by ireneshusband on 2007-10-28
I need to upgrade to gutsy on one of our machines, but the upgrade doesn't appear to be available by apt-get, aptitude, adept or synaptic. I have double and triple checked that the system is up to date (aptitude update and aptitude upgrade), but there's still nothing doing. When I try aptitude dist-upgrade it tells me that there are no packages  to upgrade, in adept the upgrade button is greyed out and synaptic doesn't do whatever it is supposed to do either.

Anyone know how I can get round this?

---

### Post by khughitt on 2007-10-28
Try running **update-manager**. If that doesn't work, post the contents of your /etc/apt/sources.lst file.

---

### Post by ireneshusband on 2007-10-28
> **pwnedd said:**
> Try running **update-manager**. If that doesn't work, post the contents of your /etc/apt/sources.lst file.

Thanks! update-manager at least recognises that there is a new version. Haven't tried upgrading yet though. Will leave that until tomorrow.

---

### Post by khughitt on 2007-10-28
No problem. Goodluck! :)

---

