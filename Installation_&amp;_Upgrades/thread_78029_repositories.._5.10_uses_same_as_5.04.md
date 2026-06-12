---
title: "repositories.. 5.10 uses same as 5.04??"
date: 2005-10-17
forum: Installation &amp; Upgrades
---

### Post by floyd27 on 2005-10-17
Do I add the same repo's as the 5.04 ones..
basically I guess what im asking is, Is th e Guide for 5.04 Ok/good/safe to use for 5.10?

Is there a new guide that I dont know about for 5.10..
thanx guys..

---

### Post by seldenthuis on 2005-10-17
> Do I add the same repo's as the 5.04 ones..

Nope. The Breezy backports are not (and will not be) hosted on mirrormax.net. In fact, they are not even online yet, so you should comment them out in sources.list.

You do have to add the multiverse lines in order to get programs like acroread, flash etc.:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

The Unofficial Ubuntu 5.10 Starter Guide is not yet available. Most of the things in the old guide are still correct for Breezy though.

---

### Post by floyd27 on 2005-10-17
so, add those 2 you listed, and comment out the rest?
Im not sure..?

---

### Post by SickTwist on 2005-10-17
[QUOTE=floyd27]so, add those 2 you listed, and comment out the rest?
Im not sure..?[/QUOTE]

In a terminal type:

sudo gedit /etc/apt/sources.list

For every line that starts with "deb" or "deb-src" (without the quotes) change the word "hoary" to "breezy" (again, without quotes). Save the file and close gedit. Then in the terminal type:

sudo apt-get update

---

