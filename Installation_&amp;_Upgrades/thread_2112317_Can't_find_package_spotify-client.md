---
title: "Can't find package spotify-client"
date: 2013-02-04
forum: Installation &amp; Upgrades
---

### Post by JeyPeyy on 2013-02-04
I made a frech install of ubuntu 12.10 not long ago and now I wanted to install spotify on it. So I added the repository to /etc/apt/sources.list, added the gpg key and updated. But when I typed "sudo apt-get install spoti <tab>", nothing came up. apt is unable to locate package spotify-client.

When I update, I get hits on "http://repository.spotify.com stable InRelease", "http://repository.spotify.com stable/non-free Sources", "http://repository.spotify.com stable/non-free amd64 Packages" and "http://repository.spotify.com stable/non-free i386 Packages". So where's the problem?

---

### Post by JeyPeyy on 2013-02-04
Please help. Is there a problem with spotify's repos?

---

### Post by JeyPeyy on 2013-02-05
Solved it. Removed the spotify line in sources.list, updated, put the line back and updated again.

Weird **** happens

---

