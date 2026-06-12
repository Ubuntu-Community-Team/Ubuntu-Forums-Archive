---
title: "CUPS upgrade in 7.10 has conflict"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by jazzybob on 2007-10-04
Trying to install updates through update manager and the CUPS update will not install stating that it tries to over write another file:

E: /var/cache/apt/archives/cupsys_1.3.2-1ubuntu4_i386.deb: trying to overwrite `/usr/share/doc/libcupsys2/CREDITS.txt', which is also in package libcupsys2

I have rebooted and still receive same message  Comments?

---

### Post by Haegin on 2007-10-04
This is a known problem and searching the forums would probably have got you a solution faster than waiting but here it is:

```

sudo dpkg --force -i /path/to/downloaded/deb/in/apt/cache
sudo apt-get -f install

```

Apt downloads the deb packages and saves them in a cache so you need to force install the package from there.

Sorry I can't provide the exact path but it is somewhere in /var/cache/apt I think. I am setting up my Dad's Vista machine at the moment so I can't check it for you.

---

### Post by mike984 on 2007-10-04
Try

sudo dpkg -i --force-overwrite /var/cache/apt/archives/cupsys_1.3.2-1ubuntu4_i386.deb
sudo apt-get -f install

---

