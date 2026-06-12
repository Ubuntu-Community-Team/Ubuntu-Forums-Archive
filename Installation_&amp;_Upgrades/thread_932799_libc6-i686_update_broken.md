---
title: "libc6-i686 update broken"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by lazer on 2008-09-28
I recently used adept to do an update.  It downloads a new version of libc6-i686.
Installed 2.7-10ubuntu3
Candidate:  2.7-10ubuntu4

Unfortunately the candidate version is broken.  Tried sudo apt-get clean and redownloaded it....still showing as broken.  I'm running Hardy.

---

### Post by lazer on 2008-09-29
Anyone?  I'd like to figure out what happened and how and I can fix it.

---

### Post by zvacet on 2008-09-29
```
sudo apt-get -f install
```

---

### Post by lazer on 2008-09-30
Fixed it.  Apparently, the upgrade was going to break a dependency or something to that effect.  I had tried removing libc6-i686 but it required the removal of ubuntu-minimal, which sounded like a bad thing to remove if I wanted to boot up again.  But being bored and wanting to get rid of the constant reminder that I had an update waiting, I sucked it up and removed the libc6 package and the ubuntu-minimal.  I then went back into adept and added both.  And boom they installed just fine.  So who knows, but I fixed it.

Once again proving:  I AM AWESOME!

---

