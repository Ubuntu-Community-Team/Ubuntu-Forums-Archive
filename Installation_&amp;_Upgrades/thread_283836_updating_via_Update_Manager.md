---
title: "updating via Update Manager"
date: 2006-10-24
forum: Installation &amp; Upgrades
---

### Post by leveliv on 2006-10-24
here is what I get when I try to update via Update Manager: ```
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/source/Sources.gz Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/source/Sources.gz Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/binary-i386/Packages.gz Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/binary-i386/Packages.gz Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/source/Sources.gz Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/source/Sources.gz Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)

```

How do I get rid of that so I can do my upgrade?

---

### Post by janbockaert on 2006-10-24
if you speek french, you should check out the freecontrib.org site, there seems to have been a problem with their repositories.

or you may trie to build a new sources.list. But be carefull with that, make sure all your installed applications are in the new repositories.

this tool: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic) is very nice, and it covers almost every program available for ubuntu. At first sight, it looks like the repositories you can't acces are rather standard, so i guess it is safe to build a new sources.list with source-o-matic

---

