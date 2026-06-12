---
title: "Breezy to Dapper upgrade nightmare!"
date: 2006-07-07
forum: Installation &amp; Upgrades
---

### Post by geek.de.nz on 2006-07-07
I just upgraded my breezy with dist-upgrade (apt-get) and had all sorts of problems. Now it's working fine, but it took me at least a day to fix it.

I had a custom kernel (2.6.16.9 with suspend2 support) and the nvidia module (8162) installed before and it was working fine. After the upgrade not even my X server was working.

After an administrative nightmare with installing the newest kernel (2.6.17.3 with suspend2) and reinstalling the nvidia drivers. I had to manually copy them to /usr/lib/xorg/ after install because of the following error:
```

(EE) Failed to load module "glx" (a required submodule could not be loaded, 0)
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

```

Also, I had to rename the module to <something>.so, because it was also not found...


Anyway, my KDM is still not working and I had to install gdm to be able to log in to KDE. The Failsafe is still working with KDM. Does anyone have an idea why?

---

### Post by angkor on 2006-07-07
If you have a custom kernel and built your own nvidia drivers it's normal it doesn't work anymore after a kernel upgrade.

Normally you can fix that by reinstalling the nvidia driver (the driver has to match the kernel your running).

I experienced the same problem with gdm/kdm. But with me it was the other way around. Gdm stopped working and I need to install kdm to be able to boot into gnome. Sadly I have not been able to fix it.

Can you post the output of cat ~.xsession-errors when you try to log in using kdm?

---

