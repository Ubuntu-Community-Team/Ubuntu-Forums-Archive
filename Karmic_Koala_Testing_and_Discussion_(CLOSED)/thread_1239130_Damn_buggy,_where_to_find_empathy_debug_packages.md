---
title: "Damn buggy, where to find empathy debug packages?"
date: 2009-08-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Joe_Bishop on 2009-08-13
Empathy is frequently crashing for me, have got core dump, but it's useless without symbols. Where can I find debug packages for this? I'm using the following repos for telepathy/empathy/gstreamer.
# Telepathy
> deb [http://ppa.launchpad.net/telepathy/ppa/ubuntu](http://ppa.launchpad.net/telepathy/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/telepathy/ppa/ubuntu](http://ppa.launchpad.net/telepathy/ppa/ubuntu) jaunty main
# Empathy daily
deb [http://ppa.launchpad.net/amoog/empathy-daily/ubuntu](http://ppa.launchpad.net/amoog/empathy-daily/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/amoog/empathy-daily/ubuntu](http://ppa.launchpad.net/amoog/empathy-daily/ubuntu) jaunty main
# Gstreamer ppa
deb [http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu](http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu](http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu) jaunty main
I'm catching for this bug: [http://bugzilla.gnome.org/show_bug.cgi?id=585076](http://bugzilla.gnome.org/show_bug.cgi?id=585076)

---

