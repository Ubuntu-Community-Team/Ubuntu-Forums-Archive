---
title: "gpg keys for respitories"
date: 2007-03-09
forum: Installation &amp; Upgrades
---

### Post by Phantom784 on 2007-03-09
I just updated my sources.list using the source-o-matic ([http://www.ubuntu-nl.org/source-o-matic/)](http://www.ubuntu-nl.org/source-o-matic/)).  However, I'm not sure how to import the GPG keys.  Hex values are given in the generated comments, but what should I do with them?

---

### Post by zvacet on 2007-03-09
```
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
```
Replace KEY with number

---

