---
title: "Could not download all repository indexes"
date: 2011-06-27
forum: Installation &amp; Upgrades
---

### Post by fleamour on 2011-06-27
"Failed to fetch ppa.launchpad.net/user/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz 404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead."

Are servers down?  This is like an official repo no?  My package info is 41 days old.

---

### Post by doas777 on 2011-06-27
wait a while and try again. it happens to me every couple months.

---

### Post by Toz on 2011-06-27
That PPA no longer exists. Goto [http://ppa.launchpad.net/]("http://ppa.launchpad.net/") and have a look - there is no **user** directory. If you remember for which product you added that PPA, you'll need to investigate to find out the new PPA address and add it in its place.

To fix the error message, remove that entry from your sources. A similar problem, with a fix, was reported here: [http://ubuntuforums.org/showthread.php?t=1497195]("http://ubuntuforums.org/showthread.php?t=1497195")

---

### Post by fleamour on 2011-06-28
OK, thanks, will purge PPA.  Thought it an official one but obviously added years ago for a long forgotten reason.  Cheerz.

---

### Post by fleamour on 2011-06-28
Thing is I'm not seeing a relative entry in Software Sources/Other Software?

---

### Post by fleamour on 2011-06-28
Found the blighter!

---

