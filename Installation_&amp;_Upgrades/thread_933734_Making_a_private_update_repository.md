---
title: "Making a private update repository"
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by null-cipher on 2008-09-29
I am looking to create a repository on the server at work.
I was just wondering if this is difficult to do, I believe the server is running CentOS.
The reason for hosting the server, is it becomes cumbersome and costly to install updates and common programs over the internet.

My thoughts would be the easiest way to do this would be to do updates, and copy the cache to the repo.
If possible, I would like to make it so that it would automatically download the latest updates from the main repository into this private repo.

Any help would be appreciated.

---

### Post by Partyboi2 on 2008-09-29
Maybe [[COLOR=Blue]apt cacher [/COLOR]]("http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher")will meet your needs.

---

