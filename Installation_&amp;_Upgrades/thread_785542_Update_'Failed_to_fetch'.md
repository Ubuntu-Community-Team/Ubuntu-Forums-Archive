---
title: "Update 'Failed to fetch'"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by oserdavid on 2008-05-07
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  

That's what it says when using update manager. Might this simply be because the server/repository is so busy, or might it be because there is something wrong with my Hardy Heron installation-via-Wubi 8.04?

If the latter - what do I need to do (complete beginner, me) to rectify?
David

---

### Post by Stevko on 2008-05-07
It is because the server is busy - you can try to open the link in browser and you will see that it takes very long or it even does not work.
So you either wait or you can change the server from which you download updates/packages. You can go to System-> Administration -> software sources and change the server in "Download from" menu to try faster server if you want.

---

