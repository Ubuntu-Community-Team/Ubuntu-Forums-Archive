---
title: "APT preferences"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by rowan on 2007-04-23
I have a set of packages I'd like installed from Debian testing, but I'm having trouble configuring my /etc/apt/preferences file correctly. I've installed the packages, but the Update Manager wants to upgrade to the feisty versions. I've tried various Pin-Priority levels, but it doesn't seem to make a difference. Grateful if anyone could tell me where I'm going wrong.
```

Package: *
Pin: release o=Ubuntu
Pin-Priority: 50

Package: *
Pin: release o=Debian
Pin-Priority: 40

Package: apache (and some other packages)
Pin: release o=Debian,a=testing
Pin-Priority: 1100

```

---

### Post by rowan on 2007-04-23
scratch that, giving each package a separate entry seems to have worked, but has lead me to another issue.

Update manager now shows 'apache'  as an available update from version 1.3.24-4.1 to 1.3.24-4.1 which does not make much sense. Letting it install the package has no effect.

Any ideas?

---

