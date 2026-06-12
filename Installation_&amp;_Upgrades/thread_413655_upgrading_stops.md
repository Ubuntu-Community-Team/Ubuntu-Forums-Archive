---
title: "upgrading stops"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by zumbi77 on 2007-04-19
I started the upgrade but then I get an error message:

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2) Underprosessen bzip2 ga en feilkode (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2) Underprosessen bzip2 ga en feilkode (2)

Which in english is something like: subprocess bzip2 gave an error code (2).

What do I do now?

---

### Post by kellemes on 2007-04-19
try again?

---

### Post by zumbi77 on 2007-04-19
Already tried several times

---

### Post by aashay on 2007-04-19
Good thing this was already posted coz i'm getting the very same error
Trying again doesnt help either because from what i understand, the update manager has cached the files onto disk... so when i "try again" , instead of downlading a fresh copy, it just gets the corrupted(?) one from the cache.
EDIT: THis comes up in the "modifying software channels" portion of the upgrade
EDIT AGAIN: Okay, i tried for the 5th time now... i'm getting a different error ```
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz Sub-process gzip returned an error code (1)
```
The error code changed from 2 to 1

---

### Post by kellemes on 2007-04-19
Don't know about this issue.. the only thing I can think of is the particular servers have issues at the moment..
Maybe you should try the ftp servers instead? Or some other mirror?

---

### Post by OsakaWilson on 2007-04-19
Same error over here. Tried over and over.

---

### Post by aashay on 2007-04-20
Is there a solution? Or is downloading and burning the entire 700mb iso the only option?

---

