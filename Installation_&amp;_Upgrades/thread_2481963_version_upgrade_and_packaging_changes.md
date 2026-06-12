---
title: "version upgrade and packaging changes"
date: 2022-12-14
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2022-12-14
when upgrading Ubuntu from version XX.YY to version XX.ZZ (where YY < ZZ) there may be one or more packages that are part of re-organizing into a greater number of packages where a package previously known as "xyzzy" is now split into 2 (or more) packages now known as (for example) "xyzzy-foo" and "xyzzy-bar".  what i am wanting to find is a documentation that lists all such changes in XX.ZZ since XX.YY (including the most recent previous LTS version for a new LTS version).  although not essential for my needs, if this document also lists removed and added (new) packages, that would be a plus.  any ideas what name this document would have in Ubuntu?

[SIZE=1]requests to see my source code will be considered to be spam.[/SIZE]

---

### Post by MAFoElffen on 2022-12-15
Do an Ubuntu package search then look at the change list... I think that is what you are trying to describe right?

For example, for lsb package in jammy: [https://packages.ubuntu.com/jammy/lsb](https://packages.ubuntu.com/jammy/lsb)

And in the right of that page, you will find a link to the changelog: [http://changelogs.ubuntu.com/changelogs/pool/main/l/lsb/lsb_11.1.0ubuntu4/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/l/lsb/lsb_11.1.0ubuntu4/changelog)

---

