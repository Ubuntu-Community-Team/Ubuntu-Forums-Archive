---
title: "2 Broken packages...Cant install updates/software"
date: 2006-10-21
forum: Installation &amp; Upgrades
---

### Post by thelinux_guy on 2006-10-21
I just updates my indexes for which I download software from,After this,I was warnd the I have 2 broken packages on my system and advised to remove them,How do I remove them? Because of this,I cant install any updates or any new software...

---

### Post by taurus on 2006-10-21
Open a terminal, Applications -> Accessories -> Terminal, and type

```

sudo aptitude remove <package name>
sudo aptitude update

```

---

