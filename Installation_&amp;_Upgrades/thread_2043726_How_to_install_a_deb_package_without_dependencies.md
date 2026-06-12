---
title: "How to install a deb package without dependencies?"
date: 2012-08-17
forum: Installation &amp; Upgrades
---

### Post by amirjadidi on 2012-08-17
Hi,
I have Ubuntu 12.04 (x64) platform. TexLive 2012 is installed from DVD (not from ubuntu repositories).
when I want to install TexMaker, it depends on the old texlive version on the repository. I don't want these outdated stuffs. Why the software center does not recognize that these dependecies (texlive and related stuffs) are available?

---

### Post by darkod on 2012-08-17
What exactly do you expect software centre to recognize?

If there is own repository for some software, add that repository to your ubuntu system. Then software centre will search it too.

Otherwise, it is limited on searching only the existing repositories and offering the latest version existing there.

---

### Post by unevenflow on 2012-08-17
Hey, you could try

sudo apt-get install --no-install-recommends package_name

---

