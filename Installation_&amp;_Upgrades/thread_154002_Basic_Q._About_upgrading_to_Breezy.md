---
title: "Basic Q. About upgrading to Breezy"
date: 2006-04-02
forum: Installation &amp; Upgrades
---

### Post by cd-r80 on 2006-04-02
Hi! If I upgrade from Hoary to Breezy. Is it faster or slower? Heavier or lighter? (Using already slow Gnome).I use LILO, can I choose it when upgrading. Can I cut off  programs during the upgrade: All games etc?

---

### Post by Sef on 2006-04-02
What are your system specs?  How fast really depends on them.  If you are slow, perhaps xubuntu would be faster for you.

---

### Post by cd-r80 on 2006-04-02
AMD 750Mhz, 128MB. I have used Blackbox, but I don't like it.

---

### Post by Sef on 2006-04-02
I'd recommend a server install then at the prompt:

sudo apt-get update

sudo apt-get install xubuntu

It will work faster than Gnome.  Not as fully featured, but see if it is to your liking.

Note: to do a server install, at the prompt on install, type server, then hit enter.

---

### Post by cd-r80 on 2006-04-02
I cannot find the packet Xubuntu for Hoary? I have:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe m$
and more...

---

### Post by Sef on 2006-04-02
it should be in synaptic or command line like i wrote last post.  Would not be in restricted packages.

or Applications > Accessories > Terminal from Ubuntu.  Then type in the two commands.

---

### Post by cd-r80 on 2006-04-02
Yes I understand basic command things. But perhaps I have very old apt.list I have these with some 404 not found errors when apt-get update (And pkg xubuntu not found later...):
 
deb [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://fi.archive.ubuntu.com/ubuntu](http://fi.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by cd-r80 on 2006-04-02
Ok I understood. It is only for Breezy.

---

