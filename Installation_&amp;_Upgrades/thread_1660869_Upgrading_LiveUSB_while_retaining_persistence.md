---
title: "Upgrading LiveUSB while retaining persistence"
date: 2011-01-05
forum: Installation &amp; Upgrades
---

### Post by radioactive28 on 2011-01-05
I presently have a Karmc *LiveUSB* with a casper-rw partition, but am thinking of changing the LiveUSB image to Maverick, while still using the existing casper-rw partition and its data (mostly settings for Ubuntu itself, haven't installed any programmes). Using usb-creator, by the way.

Are the config files for Karmic and Maverick significantly different that this will cause any major problems?


[Separately, I think this will have implications for my existing Karmic *install*, because I'm planning to clone my Karmic /home partition to a fresh Maverick install. Any thoughts?]

Thanks

---

### Post by C.S.Cameron on 2011-01-06
I have not had any luck using an existing casper-rw partition after an upgrade of a disk image install.
I do believe that you can reuse a home-rw partition form one disk image install to another.

---

### Post by radioactive28 on 2011-01-07
Thanks for the reply, C.S.Cameron. That prepped me in case something went wrong, because I went and upgraded the image anyway, without wiping casper-rw.

Maverick booted into persistent mode without any apparent problem, retaining my previous settings (such as volume muting), although the link to ubiquity on the desktop still said "Install Ubuntu 9.10"

It occurred to me later to look at casper-rw's content outside of persistent mode. It contained the major configuration folders such as /etc and /var with all the usual files inside, in addition to /home. I suppose it wouldn't have been a good idea to keep casper-rw in-between the different versions though, in case some major system utility was changed.

---

