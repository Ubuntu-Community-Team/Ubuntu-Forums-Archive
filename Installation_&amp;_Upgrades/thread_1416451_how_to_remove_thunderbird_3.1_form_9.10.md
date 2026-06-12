---
title: "how to remove thunderbird 3.1 form 9.10"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by insp on 2010-02-26
dear all,
i have installed thunderbird 3.1(shredder) in my ubuntu 9.10(Karmic) but i don't want to keep it any more, so i want to uninstall it from my system, but i don't know how to uninstall it.
Please Help....
i am already using thunderbird 2 on karmic

---

### Post by khelben1979 on 2010-02-26
It depends on how you installed it. If you installed as a package you should be able to see it in [Synaptic Package Manager]("http://en.wikipedia.org/wiki/Synaptic_package_manager") and uninstall it from there.

---

### Post by dannymichel on 2010-04-18
im still trying to figure out how to install 3.1

---

### Post by spydeyrch on 2010-04-18
To uninstall, try this: open a new terminal, type in (don't type in the "code" part just what follows) 

code:

apt-get remove thunderbird-3.1 thunderbird-3.1-gnome-support

to install thunderbird 3 try this (asumming you are running 9.10)

code:

sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa

sudo apt-get update

sudo apt-get install thunderbird-3.1 thunderbird-3.1-gnome-support


That should work. :KS

-Spydey:guitar:

---

### Post by Click-dot-Bejo on 2010-04-18
wanna eazy solution?
Go to Ubuntu Software Center, Search "Add/Remove Applications".
Install that software..
then after finished install, go to System > Administration > Add/Remove Applications.
Search Thunderbird 3.1
Uncheck [v] -> [ ] > then click "Apply"..

---

### Post by wilee-nilee on 2010-04-19
> **dannymichel said:**
> im still trying to figure out how to install 3.1

This ppa will dump it in synaptic for you to install. This is a daily build so if you don't want continues updates or a upgrade of firefox just load it to the apt-source list then do a update go to synaptic install shredder, then go to software sources and tick off the ppa in other software. It is likely that it will show upgrades for firefox so use your best judgment.
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

---

