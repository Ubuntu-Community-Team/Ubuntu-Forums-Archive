---
title: "Updates on a LAN"
date: 2006-08-06
forum: Installation &amp; Upgrades
---

### Post by voltagex on 2006-08-06
Hi.
I've now got 3 machines running Ubuntu nicely. My problem is that I have a download quota, and doing the updates on all of them is wasting time and bandwidth.

Is there a way I can have the updates downloaded to one computer, then distributed to the others?

My current "solution" involves copying the /var/cache/apt/archives folder to the other two computers.

Back when I was using Debian it was suggested I use the apt-proxy program to do this but I had so many problems with it that it just wasn't worth the hassle.

A way I've thought of doing it would be to run something like the scanpackages script on one computer, then have the others point to an FTP running on it.

---

### Post by eXisor on 2006-08-06
TBH I don't know, but can't you use 'rsync' to keep the /var/cache/apt/archives folder synced across the machines?

---

### Post by voltagex on 2006-08-06
I found rsync confusing, I have used an app called unison in the past. I'll do that then (either rsync or unison).

---

