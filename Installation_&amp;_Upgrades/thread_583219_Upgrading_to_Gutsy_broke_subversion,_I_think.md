---
title: "Upgrading to Gutsy broke subversion, I think"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by mattucf on 2007-10-20
After upgrading to Gutsy, I can't do any svn command that accesses a particular [older -- Debian Sarge era] repository.  This is the error I get:


svn: Cannot allocate memory
svn: bdb: unable to allocate memory for mutex; resize mutex region

Access to the old repository worked just fine in Feisty.  I can also do checkouts and commits on the newer [feisty-created] repositories just fine.  What's going on?

---

### Post by mattucf on 2007-10-21
[In case anyone else had this issue...]

Even though the error doesn't say to do so, running svnadmin recover on the old repository  seems to have fixed it for me.

---

