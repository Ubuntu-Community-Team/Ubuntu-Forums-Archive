---
title: "No password to mount drives in session"
date: 2009-11-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Regenweald on 2009-11-11
I just did a double take, clicked on my ntfs drive and it simply mounted in a fraction of a second. No password required. Now i have not checked into the release notes of the relevant package, but I consider this a serious enhancement. I am very pleasantly surprised. Hope this is intentional. The -32 kernel is working wonderfully also.

---

### Post by cdEWoozy on 2009-11-12
[https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/465054](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/465054):
```
  [ Martin Pitt ]
  * Add debian/local/ubuntu.pkla: Allow passwordless file system operations
    for local foreground admin user sessions on Ubuntu. Install it in
    debian/rules. (LP: #465054)
```

It is intentional :)

---

### Post by ronacc on 2009-11-12
on my sys it asks for a password for the first drive I mount but not ones after that , none of my drives are ntfs .

---

### Post by VMC on 2009-11-12
Your right. No more password required! Good news. I wonder if the kernel change log you list this change or some other updated file.

---

### Post by Kevbert on 2009-11-12
No passwords. Must set a password for screensaver otherwise if you leave the machine all drives are accessible by anyone.  What about remote access ?

---

### Post by Regenweald on 2009-11-12
> **cdEWoozy said:**
> [https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/465054](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/465054):
```
  [ Martin Pitt ]
  * Add debian/local/ubuntu.pkla: Allow passwordless file system operations
    for local foreground admin user sessions on Ubuntu. Install it in
    debian/rules. (LP: #465054)
```

It is intentional :)

Thanks for the research link :) this is **GREAT**. Sometimes, the little things make a big enhancement, now the only drive that needs to be manually added to fstab is the one with my music.

I must test to see if launching exaile invokes mounting of a drive, or if my library will still go missing if it's not mounted at the beginning of the session.

---

### Post by cszikszoy on 2009-11-12
Very awesome!  Entering a password every time I mount a disk on karmic is getting a little old.

---

