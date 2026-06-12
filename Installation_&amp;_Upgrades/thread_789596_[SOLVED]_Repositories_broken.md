---
title: "[SOLVED] Repositories broken?"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by Zalbor on 2008-05-10
For a week or so now, I can't update the package information from the repositories. I've tried a few different mirrors, including the one closest to me and the main server:
```
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-backports/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.
```
As a result, an icon keeps appearing that tells me I've not updated in a week.

Are the repositories broken? If so, do we know what caused it and when they're expected to be back?

The other possibility is that something's wrong on my end, but that sounds unlikely since I've tried many servers...

---

### Post by Rallg on 2008-05-10
About 6 hours ago, I did a fresh install of 8.04 i386 from CD, then connected for updates via cable. No problem. Of course, that wasn't necessarily using the same repositories.

---

### Post by Pumalite on 2008-05-10
Check your connection first. If OK.; go to: System>Administration>Software Sources>Download From>Other>Let it choose the best for you.

---

### Post by Zalbor on 2008-05-10
My connection is OK (or I wouldn't be posting actually), and like I said I've tried different servers, including letting it choose the best one...

---

### Post by Pumalite on 2008-05-10
Ok.

---

### Post by Zalbor on 2008-05-10
By the way -I have some 3rd party repositories as well (canonical, medibuntu, winehq) and none of them have a problem.

---

### Post by Zalbor on 2008-05-11
Does anyone have an idea?

---

### Post by Zalbor on 2008-05-11
I guess it was a corrupted sources.list file, although how that happened I have no idea.

I renamed the file and let Synaptic create a new one, and it worked now.

---

