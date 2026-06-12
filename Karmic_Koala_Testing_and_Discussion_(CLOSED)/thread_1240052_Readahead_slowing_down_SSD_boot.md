---
title: "Readahead slowing down SSD boot"
date: 2009-08-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by infamousrev on 2009-08-14
While tuning my boot performance I noticed that karmic boot includes a program called readahead.

> Readahead

Many files are accessed during boot. These files are accessed in the order in which they are needed, which may not match the order in which they are stored on disk. In order to speed up file access, the readahead service attempts to read these files in disk order and load them into memory before they are needed.

However if to take into account that SSD cards make access time nearly irrelevant this process simply wastes time.

And after I removed readahead from my bootprocess my boot time reduced from 12 seconds to 10 seconds.


So what I am thinking is the following: Should ubuntu automatically detect the fact your using an SSD hard drive, and automatically disable readahead?

(One of the goals of karmic kaola is improving the way it handles SSD hard drives *see blueprints)

---

### Post by castrojo on 2009-08-14
I think you're supposed to replace readahead with sreadahead. I thought that was already the case in karmic.

---

### Post by MacUntu on 2009-08-14
> **whiprush said:**
> I think you're supposed to replace readahead with sreadahead. I thought that was already the case in karmic.

Seems if you already have readahead installed, it won't get replaced:

```
testuser@chaos:~$ apt-cache depends ubuntu-desktop
ubuntu-desktop
...
  Depends: readahead
    sreadahead
...
```

AFAIK the plan is to make sreadahead work with HDDs and to completely get rid of readahead (right now, using the --no-fork option, sreadahead adds six seconds to my boot time with a HDD).

---

### Post by bear24rw on 2009-08-14
how did you remove readahead from the boot process?

---

### Post by MacUntu on 2009-08-14
If you don't want it, it should be sufficient to remove the files in /etc/readahead or you could uninstall it:```
sudo apt-get purge readahead
``` If I had a SSD I'd give sreadahead a try (installing sreadhead will uninstall readahead)! :)

---

