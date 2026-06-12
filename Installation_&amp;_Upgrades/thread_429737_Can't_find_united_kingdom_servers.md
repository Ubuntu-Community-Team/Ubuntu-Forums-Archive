---
title: "Can't find united kingdom servers"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by phil_n on 2007-05-01
I'm trying to upgrade from Edgy to Feisty using the Update Manager, but after downloading the Upgrade tool it gets stuck at 41/45 packages downloaded with the error:

```
Failed to fetch http://gb.security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg Temporary failure resolving 'gb.security.ubuntu.com'
Failed to fetch http://gb.security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_US.bz2 Temporary failure resolving 'gb.security.ubuntu.com'
Failed to fetch http://gb.security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_US.bz2 Temporary failure resolving 'gb.security.ubuntu.com'
Failed to fetch http://gb.security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2 Temporary failure resolving 'gb.security.ubuntu.com'
Failed to fetch http://gb.security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_US.bz2 Temporary failure resolving 'gb.security.ubuntu.com'

```

In Synaptic there's an option to download packages from the Main server, US server and UK server. I'm on the UK server, but if I select either of the others, I can't go back except by pressing revert. Does it matter which server I use? Can I just select Main Server and see if it goes away?

/stupid newbie question.

Cheers

Phil

---

### Post by lukew on 2007-05-01
Does not matter which one you use; though a closer one should be quicker. I am downloading from gb.archive.ubuntu.com right now and it is slow, 51KB/s. Normally this rockets down at 240KB/s - 280 KB/s!! Probably just a bad time!

Luke

---

### Post by phil_n on 2007-05-01
Cool. I shall attempt to proceed then. gb.archive.ubuntu.com seems ok, gb.security.ubuntu.com doesn't resolve at all through dns (tried pinging, got "unknown host"). Thanks for the advice!

---

