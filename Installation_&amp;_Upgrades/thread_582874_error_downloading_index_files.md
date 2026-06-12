---
title: "error downloading index files"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Simage on 2007-10-20
alright, so, tried upgrading to gutsy, left for work this morning came back at noon and found a blank desktop, at some point the upgrade failed and I don't exactly know whats going on. 

took a look at the logs and found the following

```

Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz Bad header line
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz Got a single header line over 360 chars
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz Bad header line
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz Bad header line
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz Bad header line
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/debian-installer/binary-i386/Packages.gz Bad header line

```

tried a couple times since and have gotten the same errors. I have no idea what my next step on this one is. Any one have any suggestions?? ideas??

---

### Post by MDominic on 2007-10-20
I am having the same problem.  I've been trying to upgrade since yesterday, and I get the same output even when upgrading from the CD.
One difference:  the first line of my output reads: 
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz) The HTTP server sent an invalid Content-Range header

Suggestions?

---

### Post by Simage on 2007-10-20
ok... now I'm getting that one instead of the ones I was getting earlier. Is there another server we can try or something??

---

