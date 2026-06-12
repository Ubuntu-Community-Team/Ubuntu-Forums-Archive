---
title: "Trying to Install linux-686-smp"
date: 2005-10-21
forum: Installation &amp; Upgrades
---

### Post by markr on 2005-10-21
Hi,

I'm trying to install linux-686-smp on my laptop,  but whenever I issue the command

sudo apt-get install linuc-686-smp

It returnes "Couldn't find package linux-686-smp"

I asssume I have something missing from my sources.list file:

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

Any help appreciated.

Thanks

Mark.

---

### Post by Kyral on 2005-10-21
Its "linux-image-686-smp"

---

### Post by markr on 2005-10-21
I thought a linux-686-smp package existed (in fact I can see it in packages.ubuntu.co,) that ensured all relevant packaged are installed.

Or am I missing something?

---

### Post by Kyral on 2005-10-21
Hmm you are right...

Try dropping the "gb" from your source lines and then update apt and try again

---

