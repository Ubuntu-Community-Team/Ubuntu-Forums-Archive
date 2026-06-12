---
title: "Not xsplash running? Here a tip to make it work"
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by GokuH12 on 2009-09-21
Well i im in Karmic Alpha 6, i had been since alpha 3 and for some reason i couldnt see the xsplash :S, so i did this a it works again:

sudo aptitude reinstall xsplash
sudo dpkg-reconfigure kdm
and choose gdm as the session manager (i have both, kdm and gdm)

After this, reboot and bang, xsplash running again, idk if this only works with gdm or i had something wrong before

anyway, hope to help u a litle.

---

### Post by talkingwires on 2009-09-22
Well, xsplash hasn't been running on my machine because of the udev breakage, but a new version of udev just landed. I guess I'll restart and see what happens...

---

### Post by VMC on 2009-09-22
I did just the opposite. I removed xsplash in order to see all messages that flowed out during these trying times. In the end I will re-install it at some point. The upside is I have a much faster boot.

---

