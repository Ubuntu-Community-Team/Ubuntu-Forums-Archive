---
title: "Karmic RAID device mounting"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jdavis on 2009-10-27
Hello there,

I am currently running Karmic Koala RC with the following drive setup:

1x160GB drive, EXT4 containing / and /home
2x1TB drives,  EXT3 RAID1 array, mounted as /media/storage

When I start up the machine, the 'storage' drive does not auto-mount. I have to click "Places -> Storage". Once I do this I am asked for my password, I enter this, and the device will then mount OK.

I must repeat this procedure every time I reboot the machine. This can cause problems where applications are set to use files on the storage drive at boot-time.

Is there any way to force the /media/storage drive to auto-mount without having to enter my password?

thanks, Jonathan

---

### Post by jdavis on 2009-10-28
Bump...

---

