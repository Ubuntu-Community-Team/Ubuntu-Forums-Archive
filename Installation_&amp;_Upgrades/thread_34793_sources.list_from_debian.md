---
title: "sources.list from debian"
date: 2005-05-16
forum: Installation &amp; Upgrades
---

### Post by Jonas82 on 2005-05-16
I tried to add this to my sources.list. It is from a debian sources.list:

```
deb [ftp://mirrors.sunsite.dk/mirrors/debian-non-US/](ftp://mirrors.sunsite.dk/mirrors/debian-non-US/) unstable/non-US main non-free contrib 
deb-src [ftp://mirrors.sunsite.dk/mirrors/debian-non-US/](ftp://mirrors.sunsite.dk/mirrors/debian-non-US/) unstable/non-US main non-free contrib
```

But i get this error:

```
Get:13 [ftp://mirrors.sunsite.dk](ftp://mirrors.sunsite.dk) unstable/non-US/contrib Sources [20B]
Fetched 34,3kB in 3s (9462B/s)
Reading package lists... Done
W: GPG error: [ftp://mirrors.sunsite.dk](ftp://mirrors.sunsite.dk) unstable/non-US Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B629A24C38C6029A
W: You may want to run apt-get update to correct these problems
```
What does that mean, and how can I correct it. I am totally new to Ubuntu.

---

### Post by nad on 2005-05-16
You do not want to add debian sources to your ubuntu sources list.

These two distributions are not in sync. You will likely break something.

---

