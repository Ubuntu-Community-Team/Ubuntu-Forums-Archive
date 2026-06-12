---
title: "Kubuntu takes forever to boot on my machine please help"
date: 2009-04-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by swoll1980 on 2009-04-04
Before the normal boot starts it goes through this long process that looks something like 

```
[ 32.816026 ] ATA2.01 Exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 Frozen (something something) : status : {DRDY} 
``` 

This process goes on like 3 times, and takes a couple of minutes. Then it boots normaly. Anyone else have this issue? Can you help me please?

---

### Post by swoll1980 on 2009-04-05
bump

---

### Post by swoll1980 on 2009-04-05
I found out that it is caused by my second cd drive. If I unplug it the problem goes away. Does that narrow it down?

---

### Post by caryb on 2009-04-05
My laptop is the same only if I physically have a cd in the drive, it seems to spend ages reading the disk. Other than that with ext4 it boots in under 25 secs


Cary

---

### Post by novafluxx on 2009-04-06
Not sure what the problem is, but I hope you guys get a resolution asap

---

### Post by krazyd on 2009-04-06
Could be: [http://ubuntuforums.org/showthread.php?t=598837](http://ubuntuforums.org/showthread.php?t=598837)

---

### Post by swoll1980 on 2009-04-06
> **krazyd said:**
> Could be: [http://ubuntuforums.org/showthread.php?t=598837](http://ubuntuforums.org/showthread.php?t=598837)

Thanks for the hint. The errors they are getting seem to be simular. There problem was with a sata cable. Mine is a old IDE CD drive probably not compatable, or something. It works fine once it's booted, but holds the boot proccess up by 2 minutes, or so.

---

