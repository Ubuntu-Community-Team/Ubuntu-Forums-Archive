---
title: "bzip2 errors with apt-get update"
date: 2007-07-11
forum: Installation &amp; Upgrades
---

### Post by homarus on 2007-07-11
Having trouble updating my new 7.0.4 (AMD64 server) which I did as a clean install from the normal ISO image last night.

This happens for several repositories:

<quote>
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)
It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.
</quote>

My sources.list is simple:

root@mezzanine:~# cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted universe multiverse

I've been a Debian user for years.  What am I doing wrong with Ubuntu?   I've done apt-get clean already, tried pointing to different hosts, etc.  Thanks in advance...

---

