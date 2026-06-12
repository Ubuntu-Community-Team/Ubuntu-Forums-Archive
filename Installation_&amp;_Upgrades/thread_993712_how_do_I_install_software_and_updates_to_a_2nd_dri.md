---
title: "how do I install software and updates to a 2nd drive?"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by wendallsan on 2008-11-26
Hi all,

I have an eee pc with a scrawny 4 gig hard drive and an 8 gig XD card.  My 4 gig drive is full and I can't install any updates or new software.  I'd like to set things up so that files and updates take place on my XD card, which has plenty of room.  I usually use Synaptic, but also use apt-get from the command line sometimes, if the approach taken matters much.  I'm also running ubuntu-eee if that's an issue at all.  Thanks for any help that you can provide.

---

### Post by lemming465 on 2008-11-28
The main space updates squat on is /var/cache/apt.  Try making a symlink from that to the XD card.  E.g. [code]
sudu -i
apt-get clean
cd /var/cache
mv -i apt apt-old
ln -s /some/where/with/space apt
[code]

---

