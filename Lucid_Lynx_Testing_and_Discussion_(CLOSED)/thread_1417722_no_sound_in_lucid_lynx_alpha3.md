---
title: "no sound in lucid lynx alpha3"
date: 2010-02-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by fahd on 2010-02-27
There is no sound in lucid lynx alpha 3. Any help would be appreciated. Thanks.

Fahd
100227

---

### Post by Dauthi4 on 2010-02-28
Hi,

I had the same problem.

Just type
```
alsamixer
```
in a terminal and look for a low level (it was "speaker" for me).

---

### Post by kainos on 2010-02-28
> **fahd said:**
> There is no sound in lucid lynx alpha 3. Any help would be appreciated. Thanks.

Fahd
100227

Not sure if you got this taken care of or not. I had a similar problem after upgrading to Alpha 3 from Karmic. It was specific to my existing user account though. Sound worked at GDM screen and also for newly created accounts. So, I deleted .pulse in my user account and rebooted. Sound worked afterwards.

---

### Post by Trefayne on 2010-03-01
> **kainos said:**
> Not sure if you got this taken care of or not. I had a similar problem after upgrading to Alpha 3 from Karmic. It was specific to my existing user account though. Sound worked at GDM screen and also for newly created accounts. So, I deleted .pulse in my user account and rebooted. Sound worked afterwards.

This worked for me, thanks for the tip. :D

---

### Post by kainos on 2010-03-01
> **Trefayne said:**
> This worked for me, thanks for the tip. :D

Your's welcome, glad I could help.

---

### Post by cmcanulty on 2010-04-29
I have no sound also and can't see how to change the levels in the alsa mixer

---

