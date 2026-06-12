---
title: "Help with Dapper Upgrades"
date: 2006-10-10
forum: Installation &amp; Upgrades
---

### Post by n8qxb on 2006-10-10
When I run sudo apt-get update the following appears,
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

How do I get this fixed?
Thank you!

---

### Post by Kateikyoushi on 2006-10-10
Try to copy this in terminal

```
gpg --keyserver subkeys.pgp.net --recv F120156012B83718
gpg --export --armor F120156012B83718 | sudo apt-key add

```

---

