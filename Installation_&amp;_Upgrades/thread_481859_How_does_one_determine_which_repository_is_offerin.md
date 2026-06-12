---
title: "How does one determine which repository is offering an updated package"
date: 2007-06-23
forum: Installation &amp; Upgrades
---

### Post by afoglia on 2007-06-23
I've added a few repositories to my sources.list (for updated emacs snapshot and other things not in Feisty), and just today one of them began to offer an update to a package for which I'm currently using the official Feisty version.  Is there some set of apt-<something> commands that will tell me which repository is the host of this new version?

---

### Post by mikewhatever on 2007-06-23
It seems quite possible that both repositories would have the same package available. Why would you think the newest version can only be in one?

---

### Post by afoglia on 2007-10-13
> **mikewhatever said:**
> It seems quite possible that both repositories would have the same package available. Why would you think the newest version can only be in one?

Because it's an unofficial repository with an unusual version.  In particular it's libsqlite and it wants to upgrade from 3.3.13-0ubuntu1 to 3.3.13-1alex.

I had stumbled across where it was from, but I've since forgotten.  (I believe it's an emacs 22 repository, but I could be wrong.)  I've been just unselecting from the update-manager, but I'm going to remove the repository from my sources.list before upgrading to gutsy.

---

