---
title: "List explicitly installed packages"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by paddlaren on 2010-02-19
Hi!

I wounder how I should do to find out what packages I have explicitly installed on the system, NOT including the dependencies. 

The purpose is to get a figure of what packages I need to install when I reinstall my system.

In Gentoo one can look at the world-file (/var/lib/portage/world) which is a list of my explicitly installed packages, not including system packages  (located in /var/lib/portage/system).

Regards,
Erik

---

### Post by zvacet on 2010-02-19
> The purpose is to get a figure of what packages I need to install when I reinstall my system.

If you mean you want exact same system after reinstall then 

```
aptitude --display-format '%p' search '?installed!?automatic' > ~/my-packages
```

You will find text file in your home directory.Save that file on stick or mail it to yourself.After you reinstall put that file in your home folder and 

```
sudo xargs aptitude --schedule-only install < my-packages
 sudo aptitude install
```

---

