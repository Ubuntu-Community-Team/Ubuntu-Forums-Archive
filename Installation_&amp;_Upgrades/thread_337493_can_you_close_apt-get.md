---
title: "can you close apt-get?"
date: 2007-01-13
forum: Installation &amp; Upgrades
---

### Post by carverj on 2007-01-13
Hi Ho,
         Cancelled half way through an automatix2 script last night (it got as far as installing fonts!)
and now when I try to run automatix2 an the following alert appears.

> 
Apt-Get is running
Please close Apt-Get and restart Automatix


Could someone please explain to me why this is and how I would go about fixing the problem?

Cheers, your a champion!!

---

### Post by aliyanage on 2007-01-13
Hi there,

I am not really sure, but did you already try:

```
sudo killall apt-get
```

please let me know whether this worked out or not, I remember having the same issue once and I think this was what I used to solve the problem...

regards
aliyanage

---

### Post by carverj on 2007-01-13
Ha, funny.... apt-get just responded with 

> 
apt-get: no process killed


but the problem has vanished, so somehow it managed to work!!!!
Cheers Aliyanage

---

### Post by aliyanage on 2007-01-13
hehe, okay :-D funny thing, well glad it worked out...
have a good one!!!

---

### Post by nightwolf2k5 on 2007-03-17
yeah, i got the same problem and did the sudo killall get-apt.
It worked. I think this problem arises when you are already running a system tool.
Cause for me, i had started EasyUbuntu (i couldn't see it on the screen), and again tried Automatix.
And when i tried the sudo killall get-apt, a pop up for easyubuntu came up and closed it.

---

