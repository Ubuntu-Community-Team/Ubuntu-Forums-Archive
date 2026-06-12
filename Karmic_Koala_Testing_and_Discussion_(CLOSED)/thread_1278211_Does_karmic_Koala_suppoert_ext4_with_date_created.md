---
title: "Does karmic Koala suppoert ext4 with date created ?"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ubfu on 2009-09-29
As previously [http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4) , does it support timestamps?
"Ext4 also adds support for date-created timestamps" ?

Thank you

---

### Post by VMC on 2009-09-29
Ext4 supports "Improved timestamps" if that's what your referring to, and yes karmic works well on Ext4.

---

### Post by ubfu on 2009-09-29
I mean date-created timestamps ? example not just having date modified.
Able to have date created and date modified for files .

---

### Post by ubfu on 2009-09-30
Anyone know does it implement on karmic koala ?

---

### Post by Gourgi on 2009-09-30
> **ubfu said:**
> Anyone know does it implement on karmic koala ?

do you know any other distro that is implemented?

> Ext4 also adds support for date-created timestamps. But, as Theodore Ts'o points out, while it is easy to add an extra creation-date field in the inode (thus technically enabling support for date-created timestamps in ext4), it is more difficult to modify or add the necessary system calls, like stat() (which would probably require a new version), and the various libraries that depend on them (like glibc). These changes would require coordination of many projects. So, even if ext4 developers implement initial support for creation-date timestamps, this feature will not be available to user programs for now.[8]
reading Theodore Ts'o reply from here [http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4) it seems to me that there is theoretical support but not tools yet.
```
man ls 
```mentions nothing about "date created" 

So i guess the answer is no support yet.

---

