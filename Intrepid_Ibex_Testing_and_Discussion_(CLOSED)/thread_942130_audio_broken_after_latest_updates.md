---
title: "audio broken after latest updates"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by syko21 on 2008-10-08
I just updated and a whole lot of packages were upgraded and now sound does not work. I am assuming it has something to do with /dev/shm and /dev/pts not loading. On boot I was reading the scrolling text and it said something about shm and pts not existing. Then when I tried poking around in alsamixer thinking it was just a muted PCM issue there was an error
```
E: shm.c: shm_open() failed: Permission denied
E: shm.c: shm_open() failed: Permission denied
E: shm.c: shm_open() failed: Permission denied
```bug report submitted [https://bugs.launchpad.net/ubuntu/+bug/280516](https://bugs.launchpad.net/ubuntu/+bug/280516)

---

