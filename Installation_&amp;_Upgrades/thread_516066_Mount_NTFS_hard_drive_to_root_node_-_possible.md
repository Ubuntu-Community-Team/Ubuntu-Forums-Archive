---
title: "Mount NTFS hard drive to root node - possible?"
date: 2007-08-02
forum: Installation &amp; Upgrades
---

### Post by widernet_project on 2007-08-02
Hi there,
I can mount my NTFS drive to a folder ( such as /NTFS) by using ntfs-config package. But I would like to mount it to root node instead of a folder. I modify the entry in /etc/fstab:
The old one:
    /dev/sdb1 /NTFS ntfs-3g defaults,force 0 0
The new one:
   /dev/sdb1 / ntfs-3g defaults,force 0 0  (just change "/NTFS" to "/")
I restart my computer and it can never start up again (it displays an error say some thing about display problem, which is weird because if I change the entry back, it starts up normally).
So my question is "Is it possible to mount a NTFS disk to root node?". If I can, how can I do that.
Thanks.

---

### Post by merlinus on 2007-08-02
/ (root) is a linux filesystem.  ntfs is for windows.

-merlin

---

### Post by widernet_project on 2007-08-14
Did you mean the answer is "no"?

---

### Post by merlinus on 2007-08-14
Correct.  You are trying to mount a different filesystem from the one used by / onto it.

-merlin

---

