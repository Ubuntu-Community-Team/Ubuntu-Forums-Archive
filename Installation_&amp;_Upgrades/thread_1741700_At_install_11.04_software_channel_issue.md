---
title: "At install 11.04 software channel issue"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by vitriol_32 on 2011-04-28
Wondering if anyone could help me. Currently running 10.10, and when I selected upgrade to 11.04 from upgrade manager it begins the process well enough, but during the setup of the software channels it progresses to a point, then stops and tells me that I may have a transient network issue, and that it could not authenticate the following packages:

libgssapi-krb5-2
libk5crypto3
libkrb5-3
libkrb5support0

All of which are MIT Kerberos runtime libraries apparently (not that Linux saavy, looked them up in the package manager). It tells me to try this again later, but I had the same issue preventing me from trying to drop the beta over the last week. I have tried this several times over the last week (for the beta) and several times today for the actual drop. Have no other network issues that I am aware of. Thoughts?

---

### Post by Pumalite on 2011-04-28
The Servers are busy. Wait a couple of days

---

### Post by dino99 on 2011-04-28
from your sources.list: deselect all the non genuine natty repo, then clean/autoclean/autoremove the cache before updating again

note: servers are actually over charged, so patience or way a few days

---

### Post by vitriol_32 on 2011-04-28
Was hoping it was that simple. Thanks!:)

---

### Post by vitriol_32 on 2011-04-28
> **dino99 said:**
> from your sources.list: deselect all the non genuine natty repo, then clean/autoclean/autoremove the cache before updating again

note: servers are actually over charged, so patience or way a few days

How would I go about de-selecting those? Where is the sources.list? And then c/a/a? Sorry to be a bother....

---

### Post by vitriol_32 on 2011-04-28
Think I found it, but will wait a day or so then try to upgrade. Thanks!

---

