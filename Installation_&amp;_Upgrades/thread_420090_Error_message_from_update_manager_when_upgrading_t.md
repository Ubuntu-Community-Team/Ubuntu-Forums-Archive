---
title: "Error message from update manager when upgrading to feisty"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by DiscoKiller on 2007-04-23
hi all

i`m currently trying to upgrade from edgy to feisty, however when i run the update manager i get the error message:

unable to fetch [http://theli.free.fr/packages/dists/edgy/listen/binary-i386/Packages.gz](http://theli.free.fr/packages/dists/edgy/listen/binary-i386/Packages.gz) 301 Moved Permanently

anyone know how i can remedy this?

any help will be greatly appreciated


cheers

DK

---

### Post by Jussi Kukkonen on 2007-04-23
The repositories you are using have been moved (or are otherwise broken). theli.free.fr doesn't sound like a official ubuntu repository, so I assume you've edited them yourelf?

**EDIT Scratch my previous advice** -- I didn't notice the repo was just for listen. In that  case just remove the lines that are not official ubuntu repos from /etc/apt/sources.list.

---

### Post by DiscoKiller on 2007-05-01
i`ve tried renewing my repo list from an online generator, 

the one i had was from automatix!

still no joy, i`m not at my home comp right now, but i remember the error message had gone away, only to be replaced by two other ones along the same lines.

any chance i could get a working sources.list off someone?

cheers

DK

---

