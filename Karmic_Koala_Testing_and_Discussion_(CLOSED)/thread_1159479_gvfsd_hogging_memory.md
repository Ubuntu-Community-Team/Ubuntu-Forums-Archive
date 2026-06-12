---
title: "gvfsd hogging memory?"
date: 2009-05-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Neon Lights on 2009-05-14
Within half an hour, it will try to take up all 1GB of my RAM and as much swap space as possible too. o.o Killing it resets it to like, 1MB, but then it creeps back up. Happening to anyone else? How do I figure out why it's doing this? :/

---

### Post by taavikko on 2009-05-15
Might be related,
```
[   36.476016] gvfs-gdu-volume[4053]: segfault at 18 ip 00007f52f77af2f1 sp 00007fff60770a10 error 4 in libgdu.so.0.0.0[7f52f77a4000+22000]
[   39.215731] gvfs-gdu-volume[4117]: segfault at 18 ip 00007f52e81322f1 sp 00007fff694dc620 error 4 in libgdu.so.0.0.0[7f52e8127000+22000]
```

started after latest gvfs updates

just did sftp mount via gvfs, let's wait for memory leaks.

---

