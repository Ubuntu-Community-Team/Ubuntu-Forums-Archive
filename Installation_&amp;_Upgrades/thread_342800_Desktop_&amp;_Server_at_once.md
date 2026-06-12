---
title: "Desktop &amp; Server at once?"
date: 2007-01-20
forum: Installation &amp; Upgrades
---

### Post by Volcano on 2007-01-20
For a new installation, what's the best way to install the server with LAMP, plus all the desktop stuff?   Surely it can't be as easy as installing from the server CD and then from the desktop CD?

Thanks,
Ben

---

### Post by taurus on 2007-01-20
Install the desktop version and then install whatever else you need to run it as a server with synaptic/apt-get/aptitude.

Or install the server version and then install Gnome after that.

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

