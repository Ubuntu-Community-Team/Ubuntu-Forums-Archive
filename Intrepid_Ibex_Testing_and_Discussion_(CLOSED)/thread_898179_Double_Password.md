---
title: "Double Password"
date: 2008-08-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mc4100 on 2008-08-23
I believe the problem is related to recent updates to pam, I remember being asked if a config file should be overwritten (yes) and now I'm prompted for my password twice. On login I have to type it twice, in the terminal I must type it twice -- anytime it asks for a password. This makes things like ```
gksudo <whatever>
``` unusable, since the password needs to be typed twice yet the box only pops up once. The workaround is just to use sudo, and of course type the password twice, but that's bad form. I'm unsure whether it's my fault, per se (as a botched config setup), or if it's an actual bug (regardless of the config file) caused by the update. Is anyone else seeing this behavior?

---

### Post by ronacc on 2008-08-23
I am not seeing this here on amd64 , pam was updated last evening my time (east coast US ) and I checked both before and after this mornings update .

---

