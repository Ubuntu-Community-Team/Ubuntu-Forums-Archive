---
title: "Upgrade path from quite older revision"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by mailforbiz on 2007-05-29
Hi all,

After a long hiatus, I'm back to using Ubuntu for general purpose needs. I have Breezy on my system and was wondering if I want to do a network upgrade, its possible for me to go Breezy->Dapper->Edgy or just jump to Edgy (I don't think I'd want to use Feisty yet). I had to muck around quite a bit with my Breezy libraries (glibc,ssl,bbn etc for an encryption-related project) and I might prefer to do things one step at a time.

BTW, it seems using apt-get to upgrade is no longer the 'official" method. How about using Synaptics?
Thanks for your input in advance,
HT

---

### Post by aysiu on 2007-05-29
I wouldn't jump versions, and I think the time it'll take for you to do a network upgrade and the chance of there being breakage... your best bet is to just back up your important stuff (or [create a separate /home partition](http://www.psychocats.net/ubuntu/separatehome)) and reinstall Feisty Fawn.

Even on a fast connection, *one* upgrade can take several hours--an hour to download, an hour to unpack, an hour to make changes.

---

