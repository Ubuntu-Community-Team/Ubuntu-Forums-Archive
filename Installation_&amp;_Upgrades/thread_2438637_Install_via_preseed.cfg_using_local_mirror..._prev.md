---
title: "Install via preseed.cfg using local mirror... prevent proposed being added as a repo."
date: 2020-03-15
forum: Installation &amp; Upgrades
---

### Post by carrera4life on 2020-03-15
Is there any way within a preseed file to prevent the addition of a proposed entry in /etc/apt/sources.list.d/proposed.list ?

The preseed file contains

### Apt setup
d-i apt-setup/restricted boolean true
d-i apt-setup/universe boolean true
d-i apt-setup/main boolean true
d-i apt-setup/backports boolean false
d-i apt-setup/proposed boolean false

So I assumed it would not add an entry for proposed.. FWIW, this is not connected to the Internet; it's a local mirror, so with the entry in proposed.list, it tries to connect to archive.ununtu.com.. which will also fail.

Also, is there any way to prevent the *i18n* entries being generated in /var/lib/apt/lists/ ?  
Post install, I know I can add an entry to /etc/apt/apt.conf and remove the *i18n* files from the above directory..

Cheers.

---

