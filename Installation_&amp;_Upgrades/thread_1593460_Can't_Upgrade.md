---
title: "Can't Upgrade"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by cian1500ww on 2010-10-11
Tried upgrading from 10.04 to 10.10 today but I encountered the below error when I ran the update manager.

[img]http://img843.imageshack.us/img843/9886/screenshotbmv.png[/img]

---

### Post by dino99 on 2010-10-11
check your sources: synaptic repo tab
you only might have genuine maverick repo activated (desactivate ppa and all other third parties if any)

the clean the room:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo dpkg --configure -a
sudo apt-get update

---

### Post by cian1500ww on 2010-10-11
Tried that and I'm getting a new error now:

[img]http://img214.imageshack.us/img214/6407/screenshotrsq.png[/img]

---

### Post by sanderd17 on 2010-10-11
Could you try aptitude (command line) to upgrade?

```

sudo aptitude dist-upgrade

```

Aptitude is good in giving solutions like "remove A to solve this" or so.
If it doesn't work, you'll have to reason yourself and try to remove the file or the package mentioned.

---

### Post by cian1500ww on 2010-10-11
> **sanderd17 said:**
> Could you try aptitude (command line) to upgrade?

```

sudo aptitude dist-upgrade

```

Aptitude is good in giving solutions like "remove A to solve this" or so.
If it doesn't work, you'll have to reason yourself and try to remove the file or the package mentioned.
Tried that and didn't seem to have any effect, updated some things but I'm still in version 10.04. By the looks of things it must be some package that's preventing the upgrade. It mentions something about held packages but I can't see anything in synaptics :(

---

### Post by sanderd17 on 2010-10-11
Sorry, I'm kinda ecperminenting right now, what about

```

sudo aptitude full-upgrade

```

---

