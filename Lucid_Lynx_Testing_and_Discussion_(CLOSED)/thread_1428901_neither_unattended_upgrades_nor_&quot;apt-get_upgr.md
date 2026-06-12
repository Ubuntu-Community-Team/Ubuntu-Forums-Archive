---
title: "neither unattended upgrades nor &quot;apt-get upgrade&quot; works, but aptitude upgrade does"
date: 2010-03-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by robertbub on 2010-03-13
For some reason, after installing Lucid Lynx, only "aptitude upgrade" (and "aptitude safe-upgrade" and "aptitude full-upgrade") works -- neither "apt-get dist-upgrade", "apt-get upgrade", unattended-upgrade, nor synaptic will upgrade my packages nor fetch new packages.

Anyone else experiencing this problem?  I tried removing /var/lib/apt/lists and "apt-get update" repeatedly but it doesn't improve.

This certainly isn't a show-stopper, but it's annoying and confusing.

---

### Post by robertbub on 2010-03-16
It turns that I had a rogue apt preferences file (in my preferences.d directory) that set to prefer karmic releases.

Once I got rid of this, things started working again.

---

