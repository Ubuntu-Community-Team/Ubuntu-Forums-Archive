---
title: "Installed 14.04LTS, but Details still says 13.10"
date: 2014-04-17
forum: Installation &amp; Upgrades
---

### Post by newbie4 on 2014-04-17
Installed 14.10LTS, everything looks fine except under Settings, Details, it still says 13.10.

---

### Post by sammiev on 2014-04-17
> **newbie4 said:**
> Installed 14.10LTS, everything looks fine except under Settings, Details, it still says 13.10.

Notice that as well. I'm sure a few other things will come up as well.

---

### Post by su:bhatta on 2014-04-17
Hi sammiev,
I just did a update-upgrade & dist-upgrade and i get in settings "Kubuntu 14.04" KDELibs :4.13

---

### Post by sammiev on 2014-04-17
> **su:bhatta said:**
> Hi sammiev,
I just did a update-upgrade & dist-upgrade and i get in settings "Kubuntu 14.04" KDELibs :4.13

Your correct when you say Kubuntu displays 14.04
but
UbuntuGnome 14.04 displays 13.10

---

### Post by 23dornot23d on 2014-04-17
I wonder where yours is pulling its information from to get 2 separate readings .......

its usually just

> 
K53SV:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty



---

### Post by su:bhatta on 2014-04-17
Same here:
> :~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04 LTS
Release:        14.04
Codename:       trusty

I guess, Gnome has not updated it yet.
Maybe try the update, upgrade, dist-upgrade trick on it ?

---

### Post by sammiev on 2014-04-17
I'm sure the detail screen will be updated soon. :)

---

