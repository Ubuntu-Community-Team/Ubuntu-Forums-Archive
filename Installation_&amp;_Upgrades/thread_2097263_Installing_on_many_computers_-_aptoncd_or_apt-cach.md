---
title: "Installing on many computers - aptoncd or apt-cacher-ng?"
date: 2012-12-22
forum: Installation &amp; Upgrades
---

### Post by nicklear on 2012-12-22
I am a total beginner to Ubuntu and Linux in general, but I've done a bit of forum reading. I have received 3 old Win XP laptops which I am planning to install with 12.10 and give to various departments at the charity/NGO I work at. I am in Mozambique and have limited bandwidth.

I am working on the first laptop and I have installed Portuguese language support via system settings and some additional programs via the software center. Also, I installed with access to the internet, though I think I lost connection during the install. Software update wants to install 120MB of updates, which I was thinking of just ignoring, because it's working fine at the moment.

For laptops no 2 and 3, without much internet, am I better off with AptonCD or apt-cacher-ng or trying to clone the HDD?

I don't really want to clone as the hardware is/might be different.

Does apt-cacher-ng work for installing additional languages or just for software?
Does aptoncd?

Any help appreciated.

---

### Post by Lars Noodén on 2012-12-22
Regardless of which method you choose, you'll probably end up loading and reloading systems.  So I'd recommend getting apt-cacher-ng or apt-cacher set up so that experimentation with the other methods go faster.  It makes a world of difference to have the deb files cached with limited bandwidth.

---

### Post by nicklear on 2012-12-23
Is language support also stored in deb files? So if I set up apt-cacher-ng and then add a language, will it get it from the cache?

---

