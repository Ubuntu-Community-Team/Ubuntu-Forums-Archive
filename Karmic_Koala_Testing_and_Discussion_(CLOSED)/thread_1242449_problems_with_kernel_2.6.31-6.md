---
title: "problems with kernel 2.6.31-6"
date: 2009-08-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by biasquez on 2009-08-17
(like this post: [http://ubuntuforums.org/showthread.php?t=1233813](http://ubuntuforums.org/showthread.php?t=1233813))

i have these problems:

- i can't use sudo (i must use ctrl+z or ctrl+c to unlock terminal session)
- my eth0 doesn't work ( atheros AR8121)
- my wlan0 doesn't work ( intel 5000)

---

### Post by dino99 on 2009-08-17
what do you find in the logs ?
seems to be a problem with drivers; may be search about libs needed by these drivers. Install htop & see if ram is eaten by a process or cpu over used by a process.
At least, reboot in safe mode

---

### Post by biasquez on 2009-08-20
> **dino99 said:**
> what do you find in the logs ?
seems to be a problem with drivers; may be search about libs needed by these drivers. Install htop & see if ram is eaten by a process or cpu over used by a process.
At least, reboot in safe mode


logs attached ( error depends on dvb-t avermedia a309)

---

