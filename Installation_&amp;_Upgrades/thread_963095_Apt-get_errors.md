---
title: "Apt-get errors"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by awacs on 2008-10-29
Lately, apt-get update gives lots of errors like these:

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release: Internal error: Good signature, but could not determine key fingerprint?!
W: You may want to run apt-get update to correct these problems

Help!

---

### Post by Phil112 on 2008-10-29
Im guessing you've tried to run "apt-get update" and it didn't help?

---

### Post by awacs on 2008-10-29
> **Phil112 said:**
> Im guessing you've tried to run "apt-get update" and it didn't help?

Yes, as I said, I get the errors when I run apt-get update. It seems odd to me that apt-get update would tell me to run apt-get update to fix problems with apt-get update, but hey ...

---

### Post by paxmark1 on 2008-10-29
mine said "bizarre error"  never seen that one before

---

### Post by awacs on 2008-10-31
Any ideas on how to solve, anyone?

Thanks!

---

### Post by awacs on 2008-11-02
> **awacs said:**
> Any ideas on how to solve, anyone?

Thanks!

Fixed. /usr/bin/gpgv was corrupted.

---

