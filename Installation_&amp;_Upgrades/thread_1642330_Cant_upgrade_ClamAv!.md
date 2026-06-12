---
title: "Cant upgrade ClamAv!"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by dioxholster on 2010-12-10
what a horrendous piece of software. Ive been at it 3 days trying to do something that ought to be simple and everytime i solve one problem another problem arises. at first I removed the old clamav 9.5 or something. I got the latest ubuntu release btw, and Clamav used to work when i first installed it in the previous ubuntu release. anyway, it asked me to upgrade, so since synaptic doesnt have the latest, i downloaded from sourceforge. I did the whole ./configure gave me errors like need build-essentials-- which i then did, error: need zlib.dv--- I did that one too. Now two more errors that i need to fix so I can compile it. 
here:  

configure: error: User clamav (and/or group clamav) doesn't exist. Please read the documentation !


configure: WARNING: ****** bzip2 support disabled

configure: unable to compile/link with check



I'm close to giving up.

---

### Post by duceduc on 2010-12-24
The way I got through that step was add clamav as user and group

```
sudo groupadd clamav
sudo useradd -g clamav -s /bin/false -c "Clam AntiVirus" clamav
```

However, I never got the chance to install it, I got errors when I 'make check'. I wish it is on the repo. Easier to upgrade.

---

