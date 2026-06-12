---
title: "update error on adding tor to software sources"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by 10ghost on 2010-06-10
hi all
On adding this apt-line to my software sources
deb     [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <lucid> main

and click the close button it ask me to reload or cancel 
I click reload and encounter this error messages

Failed to fetch http://deb.torproject.org/torproject.org/dists/<lucid>/main/binary-i386/Packages.gz  404  Not Found [IP: 86.59.21.36 80]
Failed to fetch http://deb.torproject.org/torproject.org/dists/experimental-<lucid>/main/binary-i386/Packages.gz  404  Not Found [IP: 86.59.21.36 80]
Some index files failed to download, they have been ignored, or old ones used instead.

But i want to install tor on my system how can i resolve this problem?

---

### Post by arrange on 2010-06-10
It's not **<lucid>**, it's just **lucid**```
deb http://deb.torproject.org/torproject.org lucid main
```

---

