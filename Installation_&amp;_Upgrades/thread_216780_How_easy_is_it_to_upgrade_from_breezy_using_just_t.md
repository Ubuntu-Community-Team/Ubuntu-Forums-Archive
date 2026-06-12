---
title: "How easy is it to upgrade from breezy using just the CD"
date: 2006-07-16
forum: Installation &amp; Upgrades
---

### Post by vialick on 2006-07-16
I'll soon be upgrading my girlfriend's breezy machine as the shipit CDs just came in, but I'm wonderring how well it works. The computer is sitting away from a net connection, and even if it could be connected to the net, it has a ridiculously low download limit.

Will this be a problem? how essential are the updates since dapper was released?

*crosses fingers and hopes for a more-or-less perfect upgrade*

---

### Post by aysiu on 2006-07-16
You can do an upgrade from CD only from the Alternate (not Desktop) CD.

It will work well, and you won't really need updates, since most are security updates, and if you're not connected to the internet... well, most of those don't really matter that much.

Pop the CD in. ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_breezy
sudo nano /etc/apt/sources.list
``` Delete (Control-K) everything from the file. Then save (Control-X, Y, Enter). ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude dist-upgrade
```

---

