---
title: "Remove ppa from list"
date: 2012-01-10
forum: Installation &amp; Upgrades
---

### Post by jdb91 on 2012-01-10
```
W: Failed to fetch http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

I get this when I do an `apt-get update` which keeps giving errors when the automatic update runs.  I added it to install handbrake (obviously) but can't find out how to remove the two from the list.

---

### Post by oldos2er on 2012-01-10
Run ```
gksu software-properties-gtk
``` Look under the 'Other Software' tab and untick the appropriate boxes.

---

### Post by jdb91 on 2012-01-10
thanks

---

