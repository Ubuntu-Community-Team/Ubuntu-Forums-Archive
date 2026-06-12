---
title: "Can I install dapper from breezy live cd?"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by codypumper on 2006-06-03
Is it in any way possible to install dapper when using the breezy live cd?
(the live cd is in my only cd drive...)

---

### Post by aysiu on 2006-06-03
Unfortunately, that's one of the few ways you *can't* install Dapper.

You can install Dapper from the Breezy install CD or the Dapper live CD or the Dapper alternate CD.

---

### Post by codypumper on 2006-06-03
How do you install from the breezy install cd? You don't have to install breezy first do you?....

---

### Post by aysiu on 2006-06-03
You do have to install Breezy first, but not all the other desktop stuff, too.

Let's say, for example, you want Ubuntu Dapper (as opposed to Kubuntu or Xubuntu--though, those can be done from a Breezy install CD also).

Boot up the Breezy install CD.
Type ```
server
``` instead of just pressing the Enter key.
Go ahead and do the server install.
When it's done, log in and type ```
sudo aptitude update
sudo aptitude install base-config passwd
``` Then type ```
sudo cp /etc/apt/sources.list /etc/apt/sources.breezy.list
sudo nano /etc/apt/sources.list
``` Every time you see the word *breezy*, change it to *dapper*. Then save (control-x), confirm (y), exit (Enter). ```
sudo aptitude update && sudo aptitude dist-upgrade
``` You now have a Dapper server installation.

To get a desktop, type ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```

---

