---
title: "New to Ubuntu"
date: 2005-09-09
forum: Installation &amp; Upgrades
---

### Post by Maranatha on 2005-09-09
Hello, I am going to try Ubuntu for the first time, I have used several different linux distro's in the past, my favorite was Gentoo, but it was always taking forever for them to get the newest version of Gnome available. What I am wondering, is how Ubuntu differs from Gentoo, is it easy to upgrade to a new version, ie. such as going from breezy to whatever the next version might be? Is it as easier as doing an emerge update world that gentoo offered? Or will I have to download a new cd and install lke that? Also, do I set USE flags in a make.conf file? I'm basically just trying to get a handle on what kind of system ubuntu is, I really liked Gentoo, but like I said, I'm a Gnome user, and having to wait a month or more for Gnome 2.12 to be stable and usable is a pain. 

Thanks!
Mitch

---

### Post by rafakl on 2005-09-09
To upgrade in ubuntu to the newer version (hoary to breezy), just:

sudo apt-get dist-upgrade


(but before you only need to change in the sources.list file, all references to hoary to breezy, thats all)

---

