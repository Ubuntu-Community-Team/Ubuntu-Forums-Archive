---
title: "Upgrade to Breezy"
date: 2005-11-21
forum: Installation &amp; Upgrades
---

### Post by Robroy11976 on 2005-11-21
Hi, need some help ... i've read in one forum about the upgrade to breezy, and it says that i shoud:

* Open up Synaptic Package Manager, then

* Change your repositories to look for Breezy 

    *

      From

         URI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
         Distribution: hoary
         Sections: main restricted

      To

         [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
         Distribution: breezy
         Sections:  main restricted

Does it mean i should change all my repositories to breezy aside from the one stated above????

---

### Post by aysiu on 2005-11-21
[QUOTE=Robroy11976]
Does it mean i should change all my repositories to breezy aside from the one stated above????[/QUOTE] Yes. In fact, it's easier to do this **not** in Synaptic. Enter this in a terminal ```
sudo gedit /etc/apt/sources.list
``` or ```
sudo kwrite /etc/apt/sources.list
``` and do a find/replace of the word *breezy* for the word *hoary*. Then ```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Robroy11976 on 2005-11-21
Thanks ... i'll do that now :)

---

