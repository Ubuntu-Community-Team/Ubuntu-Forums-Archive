---
title: "conky sensors not working in natty"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by rvchari on 2011-04-29
hi guys,
atlast i downloaded 64 bit version of natty. (i m currently using 10.10 32 bit).
before i go for a clean install, i wished to test natty (the stable release) by running it from my usb stick.
i was able to boot into it and natty identified my wi-fi with a breeze. i wanted to test some configurations that i had customized in maverick.

i installed conky in natty and copied the conky script that i used in maverick. i also installed the necessary sensors. now the hitch is the sensors are unable to detect the temperature.

is it coz i am running natty from a usb stick or some bug is there in this part ?

---

### Post by rvchari on 2011-04-29
still no one got a solution ?

---

### Post by solitaire on 2011-04-29
Just noticed the same problem...

I upgraded my laptop from 10.10 to 11.04 (both 32 bit)
Fan seems to run constantly and the $acpitemp value in conky is not being picked up.

---

### Post by georgemc on 2011-04-30
Can't recall where I read it, however, it has to do with kernel changes.

Try replacing $acpitemp with ${hwmon temp 1} .

Good luck.

George

---

### Post by rvchari on 2011-04-30
> **georgemc said:**
> Can't recall where I read it, however, it has to do with kernel changes.

Try replacing $acpitemp with ${hwmon temp 1} .

Good luck.

George

hey, that worked !!!

and by the way, fan was working fine (tried that using awn sensors...

---

### Post by rvchari on 2011-04-30
i think it will be better to mark this thread as solved...

---

