---
title: "luksFormat doesn't prompt for passphrase"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by Johannes Hoppe on 2010-07-02
Hi everybody.

I got a little problem upgrading my ubuntu-nas with some storage.

I wanted to add a new harddrive to my lvm but I stuck before getting to this point.
I want my harddisc to be encrypted before adding it to the lvm.

I tried the following:
```
# sudo cryptsetup luksFormat /dev/sdb1 -y

WARNING!
========
This will overwrite data on /dev/sdb1 irrevocably.

Are you sure? (Type uppercase yes): yes

```

... and nothing happens. dmsetup ls returns nothing.

Did I miss something?
I'm glad for any hint because I'm already running out of disk space.

---

### Post by frostschutz on 2010-07-02
you typed a lower case yes when you were supposed to type an upper case YES

---

