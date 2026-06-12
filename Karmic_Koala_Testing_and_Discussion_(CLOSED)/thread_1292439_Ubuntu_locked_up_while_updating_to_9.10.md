---
title: "Ubuntu locked up while updating to 9.10"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sekinto on 2009-10-15
While updating from 9.04 (a fresh install) to 9.10 Ubuntu had a hard lock up, I couldn't move my cursor or switch to a non-graphical runlevel. When I tried to boot Ubuntu (both normally and in recover mode) it wouldn't get to the login screen, I'm assuming this is because I had to shut it down in the middle of a major update. Is there any way I can continue the update from a Live CD or something, or make my install bootable so I can finish the update?

---

### Post by wilee-nilee on 2009-10-15
Do you mean that while upgrading 9.04 to 9.10 you had a freeze up. So what we all need to know is where in the procesas it froze up it sounds like the upgrade was downloaded to your computer and it froze on the 9.10 installation is this correct.

---

### Post by sekinto on 2009-10-16
I came up with a solution myself. If anyone else has this problem they can boot from the live CD and do this:

```
sudo su
mount -o bind /dev /media/UBUNTU/dev
mount -o bind /dev/pts /media/UBUNTU/dev/pts
mount -o bind /dev/shm /media/UBUNTU/dev/shm
mount -o bind /proc /media/UBUNTU/proc
chroot /media/UBUNTU /bin/bash
dpkg --configure -a
apt-get update
apt-get upgrade
exit
```

Replace UBUNTU with the directory your Ubuntu partition is mounted in.

---

