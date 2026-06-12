---
title: "HOWTO for &quot;Clean Upgrade&quot; ?"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by convert_mrta on 2010-03-29
I anticipation of 10.04, I'm planning to upgrade from 9.04, which was my first Ubuntu install, which dual booted with Vista (and which I never went back to) :)

I've done a lot of reading on upgrade experiences of different versions and the consensus seems to be that a "clean upgrade" or "fresh install" is more stable, and less trouble-proned than an upgrade using the Upgrade Manager.  I believe the clean install entails totally blowing away my 9.04 and replacing it entirely with 10.04 

I'm looking for good documentation on how to do this.  Does it exist?  I'm particularly interested in not loosing my existing data and application configurations.  Where do they need to be to be kept safe?  There must be other considerations.  Is there a good single document for doing this?

Thanks much,

Greg

---

### Post by zvacet on 2010-03-29
> I'm particularly interested in not loosing my existing data and application configurations

Separate home partition is good solution for that.If you don´t have one make it following [this]("http://psychocats.s465.sureserver.com/ubuntu/separatehome") guide.When you are finish you will have root,home and swap partitions.During fresh install you will format root partition and install Lucid here.**You will not format home partition.**Just mark it as ext4 ( because you will make separate home in that filesystem format) and mark it as /home.**Once again,do not format it.**

---

