---
title: "how do I do this"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by PaulBarentt on 2007-08-26
hi I am working on a project which involves modifing my tv tuner driver how ever the step I got given is this rmmod saa7134 when I do that in terminal I get Module saa7134 is in use by saa7134_alsa what is going on


thanks:confused::confused::confused:

---

### Post by solar george on 2007-08-26
You will need to rmmod saa7134_alsa which appears to be the audio driver.

---

### Post by PaulBarentt on 2007-08-26
ok done that  thanks another problem as I am tring to extend my tuner card  frequency  using instructions on the internet when i go to make as instructed on the internet i get this gcc -lm -Wall -ggdb setfreq.c -o setfreq
In file included from setfreq.c:27:
/usr/include/linux/videodev.h:176: error: ‘VIDEO_MAX_FRAME’ undeclared here (not in a function)
make: *** [setfreq] Error 1

---

### Post by solar george on 2007-08-27
Have you followed the instructions in the INSTALL file?

---

