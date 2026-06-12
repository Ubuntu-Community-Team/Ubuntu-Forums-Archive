---
title: "WARNING: All config files need .conf: /etc/...."
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ozorba on 2009-10-01
I have used update-manager -d to upgrade to 9.10 beta. Everything worked nicely, except I keep on getting a large number of warning messages like the ones below during the bootup.

WARNING: All config files need .conf: /etc/modprobe.d/alsa-base
WARNING: All config files need .conf: /etc/modprobe.d/blacklist
...

I have searched the launchpad and seen that some people have had the same warning messages. But no answer!

Any idea what causes this? and what the cure is?

---

### Post by dadedo123 on 2009-10-01
The last 2 days I'm not getting any updates?

---

### Post by renkinjutsu on 2009-10-01
try
```
sudo mv /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist.conf
sudo mv /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.conf
```

---

### Post by ozorba on 2009-10-01
> **renkinjutsu said:**
> try
```
sudo mv /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist.conf
sudo mv /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.conf
```

This worked. Thanks!

---

### Post by jmmL on 2009-10-01
> **dadedo123 said:**
> The last 2 days I'm not getting any updates?

That's because we're in the middle of a beta freeze.

---

