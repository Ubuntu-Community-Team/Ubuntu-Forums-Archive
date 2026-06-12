---
title: "ecryptfs-utils possible bug"
date: 2008-06-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by soccerboy on 2008-06-30
I was testing out the package referred in this blueprint
[https://wiki.ubuntu.com/EncryptedPrivateDirectory](https://wiki.ubuntu.com/EncryptedPrivateDirectory)

When I ran
```
sudo ecryptfs-setup-confidential
```
the directory setup was owned by root.

Does anyone else experience the same behavior?  If so, does anyone know a fix for it.  I am not sure what all it does in pam to allow for automatic unlock of the ecryptfs.

---

### Post by yelo3 on 2008-06-30
I think you should execute it by a normal user!

---

### Post by soccerboy on 2008-06-30
can't make all the fstab edits and changes in pam then.

---

