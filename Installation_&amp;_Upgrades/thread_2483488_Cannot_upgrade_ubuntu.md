---
title: "Cannot upgrade ubuntu"
date: 2023-01-31
forum: Installation &amp; Upgrades
---

### Post by jacobjmaz on 2023-01-31
[COLOR=#232629][FONT=-apple-system]I am running ubuntu focal and am trying to upgrade to a newer release when i run sudo do-release-upgrade this happens does anyone know how to fix this
This is a normal desktop install.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]extracting 'jammy.tar.gz' Can not run the upgrade This usually is caused by a system where /tmp is mounted noexec. Please remount without noexec and run the upgrade again.[/FONT][/COLOR]

---

### Post by Tadaen_Sylvermane on 2023-01-31
post the output of ```
mount | grep tmp
``` and ```
grep tmp /etc/fstab
```

I'm thinking you have some custom stuff that you may not remember doing. Happens to me all the time. The error is pretty direct.

---

### Post by monkeybrain20122 on 2023-02-01
Just backup your data and do a fresh install, a lot faster and more reliable that way. For "upgrade" to be successful you have to have a pristine or close to pristine system (i.e not a lot of customization, third party stuffs and drivers) Not wanting to lose customized configurations is the biggest incentive for "upgrade" but this is also when it is least successful, so I always do fresh install.

---

### Post by ActionParsnip on 2023-02-01
The file system with /tmp on it is mounted noexec (This is good for security) but can cause issues. The Tadaen_Sylvermane's commands will help

---

