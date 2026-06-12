---
title: "No Device Mappers in /dev/mapper with dmraid"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by DarthRevan on 2007-02-26
I tried to install Edgy on an nvidia fakeraid 0, no problem one could say, with all these nice howtos on the web ... but:

```
sudo dmraid -r
```
returns:
/dev/sda: nvidia, "nvidia_baadjfbd", stripe, ok, 160836478 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_baadjfbd", stripe, ok, 160836478 sectors, data@ 0

... until here everything seems to be ok

```
sudo dmraid -ay
```
returns nothing (i don't know whether this is ok or not)
and there are no devices in /dev/mapper/ except of "control", so i can't access the raid.

dmraid 1.0.0.rc9 is my version

I found some more people having this problem on [http://www.ubuntuusers.de]("http://www.ubuntuusers.de") but no one with an answer... :(

---

### Post by nyinge on 2007-02-28
I've heard numerous times that dmraid package for Edgy is broken, but the one, rc13, in Feisty seems to be working for a lot of people, including myself.  Yes, Edgy's dmraid doesn't work for me either, though, I have an Intel raid.

I ended up installing Feisty instead.  Everything went smooth except for one glitch:  I have to wait 3 min at every reboots and issue the command "dmraid -ay" manually at the initramfs prompt.  You can find details about my problem (no resolution yet as of Feb 28, 2007) on [this thread]("http://ubuntuforums.org/showthread.php?t=371201&highlight=dmraid") that I posted a couple of days ago.

---

