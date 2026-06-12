---
title: "Ubuntu 9.10 will not boot - drops into maintenance shell"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by apjone on 2010-01-26
I am note sure if this is update related or not but last night both a work mate and myself had issues with 9.10 not booting. It appears that for some reason the root partition can not be mounted and you are dropped into maintenance mode with a simple shell. Not thinking ( dead on feet from work ) I just did 

```

fsck -a
mount -a

```

followed by CTRL+D to resume booting. This fixed the issue. I have not looked through my logs yet (probably wont be able to spot it now) to see what caused this.

Just a heads up though! :D

---

