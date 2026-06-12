---
title: "Installing Gnome Desktop..."
date: 2007-08-15
forum: Installation &amp; Upgrades
---

### Post by dgcarter on 2007-08-15
OK, so I have Ubuntu Dapper (Server Edition), and I want to install the Gnome Desktop on it, I also have an Ubuntu Dapper Desktop CD, can I install Gnome from the desktop disk?

I would prefer to do this as I have limited bandwidth and I am running low...

Thanks,
Darren

---

### Post by zvacet on 2007-08-15
You can install from disc only if it is alternate one.If it is not you can do this

```
sudo aptitude update && sudo aptitude upgrade
```

```
sudo aptitude install ubuntu-desktop
```

Install desktop version instead and in synaptic edit>mark packages by task>LAMP

---

