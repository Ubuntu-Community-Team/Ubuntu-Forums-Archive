---
title: "Install Gnome?"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by winther on 2007-03-14
I accidently removed gnome from the terminal, so now, the only thing i can start up after the logon screen is the terminal.. Is there any way i can reinstall it from the terminal, or do i need to reinstall Ubuntu complete?

---

### Post by lizzard on 2007-03-14
From terminal reinstall it with: 

```
sudo aptitude reinstall  ubuntu-desktop
```

---

### Post by zvacet on 2007-03-14
You can install it from CD
```
sudo apt-cdrom add
```
```
sudo aptitude install ubuntu-desktop 
```

---

