---
title: "trouble installing proftpd with apt-get"
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by asheville on 2007-03-01
I having trouble getting proftpd using the command sudo apt-get install proftpd.  I get a message saying that the package cannot be found.  After doing some reading I expected to be able to access the proftpd package after uncommenting the universe and multiverse repositories in the /etc/apt/source.list file but still no dice.

Any ideas?

Thanks

---

### Post by Kateikyoushi on 2007-03-01
Indeed it is in the universe repository after you uncommented did you do an update ?

```
sudo aptitude update
```

---

### Post by asheville on 2007-03-01
nope.  I'm a guber.  Thanks!

---

