---
title: "Lts"
date: 2014-04-26
forum: Installation &amp; Upgrades
---

### Post by pfeiffep on 2014-04-26
I'm really happy with Ubuntu 14.04 thus far - installed on my old Dell laptop and much newer HP tower (specs in signature).

Aside from the normal apt-get update, upgrade, clean, autoclean, autoremove sequence I perform weekly is there an operation or declaration required to take advantage of 14.04 LTS?

This from OMG Ubuntu is the reason for my question  _*'Canonical will not start notify LTS desktop users of an update until July, when the first point release (14.04.1) is set to go live.'*_

---

### Post by Iowan on 2014-04-26
As I recall, that's for those of us who might upgrade from 12.04 to 14.04.

---

### Post by TheFu on 2014-04-26
Well .. er ... no, however ... I would change that to 
* sudo aptitude update
* sudo aptitude full-upgrade
and only deal with the others occasionally. It is sometimes good to have old packages cached.

I would add that versioned backups are a requirement.  Wrote an article for Lifehacker on Ubuntu system maintenance a few years ago - here's a [more current version.]("http://blog.jdpfu.com/linsysmaint")

There are some small-ish bugs in 14.04, so I agree with waiting for a month or so to get those patched BEFORE doing an update to the 14.04 release for production systems.  I run LTS systems exclusively on my boxes.  There are (2) 10.04 servers running still, a bunch of 12.04 (20+) and just (1) netbook (Acer C720) running 14.04 (only because of hardware support).  Waiting until June is the plan before attempting any updates for the other systems.

[Why run only LTS releases?]("http://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release")

---

### Post by pfeiffep on 2014-04-26
> **Iowan said:**
> As I recall, that's for those of us who might upgrade from 12.04 to 14.04.
Thanks Iowan, that's what I understood. 

My query is focused on the next regular release in 6 months. I'm pretty certain I want to adopt LTS for my normal daily computing. 
Will I need to re-install the 14.04.1 release to fully identify my preference for LTS?

---

### Post by Iowan on 2014-04-26
> **pfeiffep said:**
> Will I need to re-install the 14.04.1 release to fully identify my preference for LTS?
No, the update process will keep your system current... as long as you allow the updates to occur.

---

