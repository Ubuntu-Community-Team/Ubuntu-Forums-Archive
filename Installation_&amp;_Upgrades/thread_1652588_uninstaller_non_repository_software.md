---
title: "uninstaller non repository software"
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by ottosykora on 2010-12-25
I just came over small problem.
When I install some software which was not taken from the official repository, that means I found somewhere a deb file, I install it, OK, but later I want remove this software.
How do I do this? I have not the synaptic 'mark for remove' function in that case.

Does there exist any kind of universal unistaller or similar tool?

---

### Post by susema on 2010-12-25
You can remove it from terminal?

```
sudo apt-get autoremove [package]
```

or;

```
sudo dpkg -r [pacgake]
```

---

### Post by karthick87 on 2010-12-25
```
sudo apt-get remove --purge <package_name>
```

---

