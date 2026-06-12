---
title: "CPU Fan Speed Not Detected"
date: 2017-02-22
forum: MINT
---

### Post by al14 on 2017-02-22
I'm booting Linux Mint 17.3 & Linux Mint 18.1 (along with some other OS's).


The 'motherboard' is a Gigabyte Z97X-UD5H-BK.


I installed 'lm-sensors' in both Linux Mint 17.3 & Linux Mint 18.1, but the 'cpu fan speed' is only displayed in Linux Mint version 18.1.


This occurs *both in Conky and in terminal when I type [sensors], re: 17.3 & 18.1.


*Mint 17.3, no cpu fan speed in Conky or terminal, mint 18.1, cpu fan speed detected and displayed in conky and terminal.


Anyone know how to resolve this?


Mint 18.1 is my main OS, but some PPA's I need programs from do not support Xenial 16.04, so I occasionally need to revert to Mint 17.3.


Thank-you,

---

### Post by QIII on 2017-02-22
Hello!

What model/manufacturer is your CPU?

Would you please post the results of 

```
sensors
```

---

### Post by al14 on 2017-02-23
It's an i5-4690K

Thanks!
[IMG]http://i390.photobucket.com/albums/oo347/bubba9191/Screenshot1_zpsaluq9oxg.jpg[/IMG]

---

### Post by #&amp;thj^% on 2017-02-23
Just maybe sensors-detect will help find  extra sensors modules that need to be loaded.
More Here: [http://askubuntu.com/questions/53762/how-to-use-lm-sensors#53782](http://askubuntu.com/questions/53762/how-to-use-lm-sensors#53782)

---

### Post by al14 on 2017-02-23
> **1fallen said:**
> Just maybe sensors-detect will help find  extra sensors modules that need to be loaded.
More Here: [http://askubuntu.com/questions/53762/how-to-use-lm-sensors#53782](http://askubuntu.com/questions/53762/how-to-use-lm-sensors#53782)

Good idea,thanks for the link!

-aL

---

