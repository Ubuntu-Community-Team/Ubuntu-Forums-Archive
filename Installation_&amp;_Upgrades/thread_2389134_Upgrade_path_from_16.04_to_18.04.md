---
title: "Upgrade path from 16.04 to 18.04?"
date: 2018-04-12
forum: Installation &amp; Upgrades
---

### Post by operator-error on 2018-04-12
When 18.04 is finalized, will there be a simply upgrade path from 16.04 to 18.04 (by simple, I mean through the Update Manager or through the terminal)? My 16.04 installation is only about 3 weeks old and I haven't done anything special to it. Doing a "clean" install is no problem, since my /home is on it's own partition, but I figured why go that route if it's basically not really necessary.

Thanks in advance for any advice.

---

### Post by SlidingHorn on 2018-04-12
> **operator-error said:**
> When 18.04 is finalized, will there be a simply upgrade path from 16.04 to 18.04 (by simple, I mean through the Update Manager or through the terminal)?  My 16.04 installation is only about 3 weeks old and I haven't done anything special to it.  Doing a "clean" install is no problem, since my /home is on it's own partition, but I figured why go that route if it's basically not really necessary.

You will most likely receive a desktop notification which will ask if you want to upgrade.  If you either don't get this, or if you decide to hold off until a later time, just do the following in a terminal:

```
sudo do-release-upgrade
```

And that should do it

---

### Post by kansasnoob on 2018-04-12
You'll be notified of the upgrade being available (via update-manager) when the first point release (18.04.1) is released in about August. Even then remember that 16.04 is supported until April 2021 so i wouldn't rush .................. if it ain't broke don't fix it ;)

---

### Post by logix2 on 2018-04-12
Before upgrading to a newer Ubuntu release, make sure all the available updates are installed.


To upgrade using a GUI, press Alt + F2 and type: 
```
update-manager -cd
```

To upgrade from the command line you can use:
```
sudo do-release-upgrade -d
```


If it still doesn't work, you can force Ubuntu to check for a newer version by running the following command:
```
/usr/lib/ubuntu-release-upgrader/check-new-release-gtk
```


From [here.]("https://www.linuxuprising.com/2018/04/how-to-upgrade-to-ubuntu-1804-lts.html")

---

### Post by operator-error on 2018-04-16
Awesome.  Thanks for the replies, everyone.

---

### Post by missmoondog on 2018-04-16
> **kansasnoob said:**
> You'll be notified of the upgrade being available (via update-manager) when the first point release (18.04.1) is released in about August. Even then remember that 16.04 is supported until April 2021 so i wouldn't rush .................. if it ain't broke don't fix it ;)

version 18.04 is due for release 26th April: Stable Ubuntu 18.04 LTS release
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

almost along the same line as OP but wondering if i have it set in repository where it says to check for updates daily and stuff, i have it set to never check as i check daily manually. will software updater still be able to notify me of new version? i update using synaptic and not software updater. will the new version just show up as a ton of updates without really "notifying" me?

darn. didn't notice this was marked as solved. should ask in a new topic then, i guess.

---

