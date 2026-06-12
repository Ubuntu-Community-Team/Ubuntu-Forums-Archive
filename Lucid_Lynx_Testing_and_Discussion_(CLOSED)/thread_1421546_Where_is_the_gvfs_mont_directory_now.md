---
title: "Where is the gvfs mont directory now?"
date: 2010-03-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Polniy on 2010-03-04
Mounted with sftp, but nothing appeared in ~/.gvfs

UPD my fault, it was fuse setup bug

---

### Post by arneko on 2010-03-11
Hello,
I'm having the same issue here and would appreciate to hear your solution. spent the last 2 hours on this without success :-(

I really need to access those folders... 

thank you in advance

Arneko

---

### Post by cariboo on 2010-03-12
The directories are always mounted in ~/.gvfs.

Open nautilus and press Crl-h to show the hidden files and directories.

---

### Post by PePas on 2010-03-26
In /etc/fuse.conf I set user_allow_other and it seemed to help.

---

