---
title: "Installing from old version Ubuntu CDs"
date: 2011-11-18
forum: Installation &amp; Upgrades
---

### Post by Nordvind on 2011-11-18
How does one install a packages from a live-CD of an old version of Ubuntu?
To be specific, I've got a 10.04 live CD (with a Broadcom driver I need), but when I launch synaptic to add repos from CD, it shows nothing in the appropriate  field.

I'm on xubuntu 11.04 now (probably doesn't matter?).

---

### Post by zvacet on 2011-11-19
I´m not sure if this is work but put CD in drive and then in terminal

```
sudo apt-cd add
sudo apt-get update
```

These commands should add CD as repo.

---

### Post by Nordvind on 2011-11-26
Actually, it's ```
apt-cdrom add
```. Nevertheless, I managed to add it, but I couldn't install any drivers, as it gave out an error in process (I no longer remember the text, some function failed). It was easier to re-install the system.

---

