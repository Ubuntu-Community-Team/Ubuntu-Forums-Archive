---
title: "sub-process /usr/bin/dpkg returned an error code (1)"
date: 2016-11-14
forum: Installation &amp; Upgrades
---

### Post by lycanthrope2 on 2016-11-14
Hi,

I'm having difficulties to update/upgrade/install any applications everything I do results in:

Processing was halted becuase there were too many errors
E: Sub-process /usr/bin/dpkg returned an error code (1)

I'm running Ubuntu 16.04 LTS

```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

```

```
sudo apt-get clean
```

doesn't help me at all.

Any suggestions?

How to remove everything and start over without reinstalling Ubuntu?

Best regards

---

### Post by Impavidus on 2016-11-14
It may be possible to fix this if you give us the complete output of those commands you tried. The first error message given is usually the most useful.

---

