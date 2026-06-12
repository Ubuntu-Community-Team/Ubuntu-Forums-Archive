---
title: "Karmic boot freezes when nfs directories are unavailable"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sanguinoso on 2009-10-11
When nfs server directories are unavailable at boot on Ubuntu Karmic my boot freezes. I have confirmed by switching the server on and off. Here are the relevant entries in my fstab

```
gryffindor:/backup /backup nfs rw 0 0
gryffindor:/srv /srv nfs rw 0 0

```Only started happening after an upgrade to Karmic

2.6.31-13-generic #44-Ubuntu SMP Sat Oct 10 15:27:55 UTC 2009 i686 GNU/Linux

Any ideas? Obvious workaround is to remove the lines from fstab and mount manually but this can be rather annoying. Also, should I submit to launchpad? I've never used it before.

---

