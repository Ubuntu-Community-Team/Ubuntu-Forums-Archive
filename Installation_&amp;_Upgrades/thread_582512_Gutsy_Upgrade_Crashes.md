---
title: "Gutsy Upgrade Crashes"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by gcvisel on 2007-10-19
The upgrade to 7.10 seems to be downloading fine until it pops up with a
"[COLOR="Blue"]Failed to fetch [http://mirror.cs.umn.edu/ubuntu/dists/feisty-security/main/binary-amd64/Packages.gz](http://mirror.cs.umn.edu/ubuntu/dists/feisty-security/main/binary-amd64/Packages.gz) Sub-process gzip returned an error code (1)" [/COLOR]message.
Then it erases all the files it downloaded, and when I try again, it has to do them all over again.

   What does that mean?  When I open a zip file, it seems to open fine...

Thanks for any help!

Gerry

---

### Post by FredB on 2007-10-20
> **gcvisel said:**
> The upgrade to 7.10 seems to be downloading fine until it pops up with a
"[COLOR=Blue]Failed to fetch [http://mirror.cs.umn.edu/ubuntu/dists/feisty-security/main/binary-amd64/Packages.gz](http://mirror.cs.umn.edu/ubuntu/dists/feisty-security/main/binary-amd64/Packages.gz) Sub-process gzip returned an error code (1)" [/COLOR]message.
Then it erases all the files it downloaded, and when I try again, it has to do them all over again.

   What does that mean?  When I open a zip file, it seems to open fine...

Thanks for any help!

Gerry

Just remove all feisty related line in your /etc/apt/sources.list with synaptic.

---

