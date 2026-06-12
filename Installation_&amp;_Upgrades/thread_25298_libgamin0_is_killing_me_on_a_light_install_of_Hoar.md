---
title: "libgamin0 is killing me on a light install of Hoary..."
date: 2005-04-09
forum: Installation &amp; Upgrades
---

### Post by scotty on 2005-04-09
Hi forumers...

I have been using Ubuntu since the start and I have a really nice looking system at work.  I also have an old PII Toshiba laptop that I have Win98 installed on half the drive.  I am trying to put a "minimal" installation of Hoary on the other side of the drive by utilizing a Miniwoody installer cd, and dropping my hoary sources.list into it from a floppy.

Anyway...I get to a point and apt-get kills me.  I start with twm and xdm.  I would LOVE to get KDE.  I install fluxbox for sanity and synaptic for ease.

When I try to apt-get install kde-core it does well until it tries to unpack libgamin0 and the kde-core install bails out.  apt-get -f install does not work.  apt-get -fm install does not work.  apt-get clean does not work.  If I delete the offending .deb from /var/cache etc. a new copy of it does not work.

Once this error happens I am stuck as apt-get can't seem to get out of its own way and get past this one offending libgamin0 deb file.  I usually need to resort to a reinstall (ugh, all those questions with debconf).

Halp!?
Scott

---

