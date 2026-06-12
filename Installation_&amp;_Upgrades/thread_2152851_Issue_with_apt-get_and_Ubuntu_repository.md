---
title: "Issue with apt-get and Ubuntu repository"
date: 2013-06-09
forum: Installation &amp; Upgrades
---

### Post by myocytebd on 2013-06-09
Years ago I can have 'apt-get whatever' done flawless.

But nowadays, it becomes a real pain that I can rarely update/upgrade without GPG annoyance (missing? obsolete?), and trying to apt-get install stuff easily lead to "Failed to fetch" or corrupted package.
(I have multiple Ubuntu versions installed)

I'm wondering do you guys keep having the same problems?


Latest problem for 13.04:
apt-get install kget
...
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/libk/libktorrent/libktorrent5_1.3.1-1ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libk/libktorrent/libktorrent5_1.3.1-1ubuntu1_amd64.deb)  Connection failed

Apparently the file is unavailable.
But seriously why does that server sucks so much? It doesn't even give a response.

Since archive.ubuntu.com resolves into multiple IPs, do you use/avoid specific IPs?

---

### Post by Cheesehead on 2013-06-09
> **myocytebd said:**
>  I can rarely update/upgrade without GPG annoyance (missing? obsolete?), and trying to apt-get install stuff easily lead to "Failed to fetch" or corrupted package.

I'm wondering do you guys keep having the same problems?

No. Not at all.


> **myocytebd said:**
> 
apt-get install kget
...
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/libk/libktorrent/libktorrent5_1.3.1-1ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libk/libktorrent/libktorrent5_1.3.1-1ubuntu1_amd64.deb)  Connection failed

Apparently the file is unavailable.

It is indeed available, and response is fast.

Perhaps you have a network issue unrelated to your Ubuntu install.

---

### Post by Toz on 2013-06-09
Changed the title of the thread to be more reflective of the issue at hand.

---

