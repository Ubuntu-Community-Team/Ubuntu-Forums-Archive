---
title: "Epiphany-webkit not in repos anymore?"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by buellman on 2009-10-05
Today I tried the 9.10 Beta Live-CD and was supprised that there was no epiphany-webkit package in the repos. Also the package epiphany-browser is msising.
Does somebody know if it was removed from the repos and if yes: why?

Greets. Buellman

---

### Post by jaxxstorm on 2009-10-05
> **buellman said:**
> Today I tried the 9.10 Beta Live-CD and was supprised that there was no epiphany-webkit package in the repos. Also the package epiphany-browser is msising.
Does somebody know if it was removed from the repos and if yes: why?

Greets. Buellman

I could be wrong, but I believe Epiphany is now completely webkit based.

Its also in Universe, have you enabled the Universe repo?

---

### Post by buellman on 2009-10-05
Hi,

this is my sources.list (removed descriptions):
```

deb http://archive.ubuntu.com/ubuntu/ karmic main universe restricted multiverse

deb http://archive.ubuntu.com/ubuntu/ karmic-updates main universe restricted multiverse

# deb http://de.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://archive.ubuntu.com/ubuntu/ karmic-security main universe restricted multiverse

```
So Universe is enabled.

This are the results from apt-get search epiphany (removed non-related packages):
```
sudo apt-cache search epiphany

epiphany-browser-data - Data files for the GNOME web browser
epiphany-browser-dbg - Debugging symbols for the GNOME web browser
epiphany-browser-dev - Development files for the GNOME web browser
epiphany-extension-gwget - Gwget extension for Epiphany web browser
epiphany-extensions - Extensions for Epiphany web browser
epiphany-extensions-more - Collection of third-party extensions for the Epiphany web browser
epiphany-gecko - Intuitive GNOME web browser - Gecko version

```

So there is nether epiphany-webkit nor epiphany-browser.

Hmmm... if you take a look [here]("http://packages.ubunut.com/karmic/gnome/") there is also no epiphany-webkit anymore.

Strange...
Greets. Buellman

---

### Post by chrisccoulson on 2009-10-05
It seems that the epiphany-webkit source has been removed now, and epiphany-browser will now be epiphany-webkit (from looking at the changelog of the latest sync with Debian).

However, epiphany-browser is currently depwait on libseed-dev, which doesn't exist in the archive yet

---

### Post by buellman on 2009-10-05
Ah... ok... so it will come back :-)
Thanks or the information!

Greets. Buellman

---

### Post by ionFreeman on 2009-10-13
I installed epiphany-browser, and got epiphany-gecko. I had to install the special epiphany-webkit instructions in this forum to get epiphany-webkit. 

I really just logged on to complain about the fact that epiphany-webkit doesn't have an 'open link in new tab' context-sensitive menu item. It's annoying.

Epiphany-gecko is, as one might imagine, a lot like Firefox. You can even install GreaseMonkey. But, it doesn't give you WebKit, so you're going to have no idea how things look in Safari.

---

