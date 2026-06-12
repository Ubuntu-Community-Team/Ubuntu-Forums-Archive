---
title: "Anyone else running into gvfsd-sftp 100% CPU usage problems?"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by altonbr on 2010-03-22
[https://bugs.edge.launchpad.net/ubuntu/lucid/+source/gvfs/+bug/538764](https://bugs.edge.launchpad.net/ubuntu/lucid/+source/gvfs/+bug/538764)

My laptop can't connect to any server and then overheats as the CPU hits 100% for too long (older laptop).

Pretty frustrating bug for me.

---

### Post by tekstr1der on 2010-03-22
Seems awfully similar to:
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/532024](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/532024)

Looks like dupes, but they're both tracking separate upstream bugs. This issue needs fixing for sure.

---

### Post by altonbr on 2010-03-23
I guess the solution for now is to type in the full URL in Nautilus and use "Forget Password Immediately" to make sure gnome-keyring (where passwords are stored) isn't accessed.

---

