---
title: "Reporting bugs in Canonical Commerical repo?"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by graeme_p on 2007-04-21
How does one report a bug in a package in the Canonical commercial repo?

There is a thread in the beginners forum about fixing problems with the Opera package in edgy commerical.

The underlying problem appears to be wrong dependencies in the package. It is not in launchpad. The Canonical site has no indication where to report bugs either.

---

### Post by graeme_p on 2007-04-24
So, from the lack of replies can I conclude that no one else has an answer to this either.

The package is still broken after several days!

---

### Post by ameba on 2007-11-21
h

---

### Post by ThrobbingBrain66 on 2007-11-21
> **ameba said:**
> hey, i know this doesn't answer your question. how did you get Canonical Commerical repo? i tried looking for it in synaptics and, i couldn't find it. My reason for looking for this repository is i think it has realplayer 10 in it.

Copy the following into your sources.list file.

## Canonical Partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

---

### Post by ThrobbingBrain66 on 2007-11-21
> **graeme_p said:**
> How does one report a bug in a package in the Canonical commercial repo?

There is a thread in the beginners forum about fixing problems with the Opera package in edgy commerical.

The underlying problem appears to be wrong dependencies in the package. It is not in launchpad. The Canonical site has no indication where to report bugs either.

Report away:
[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

For what it's worth, I had Opera installed about 3 weeks ago and everything was fine.

---

### Post by ameba on 2007-11-21
i'm

---

### Post by ThrobbingBrain66 on 2007-11-22
In a terminal:
```
gksudo gedit /etc/apt/sources.list
```
Add the 3 lines at the end of the file.  When you're done:
```
sudo apt-get update && sudo apt-get upgrade
```
Then you should be able to install Real Player.

---

