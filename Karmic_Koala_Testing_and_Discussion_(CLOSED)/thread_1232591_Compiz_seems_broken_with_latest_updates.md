---
title: "Compiz seems broken with latest updates"
date: 2009-08-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Regenweald on 2009-08-05
Anyone else ? I've removed metacity from my system altogether and use compiz and emerald. Any new developments i should be aware of ?

---

### Post by wayne_cat on 2009-08-05
some Xorg updates yesterday and today
```

lspci |grep VGA
```edit:

errors in Xorg.0.log?

```
 grep EE /var/log/Xorg.0.log
```

---

### Post by Regenweald on 2009-08-05
> **wayne_cat said:**
> some Xorg updates yesterday and today
```

lspci |grep VGA
```edit:

errors in Xorg.0.log?

```
 grep EE /var/log/Xorg.0.log
```

Thanks, GLX failed to load. Reinstall ?

---

### Post by wayne_cat on 2009-08-05
no need to reinstall ... install metacity and wait for a day or two until it is fixed

---

### Post by Regenweald on 2009-08-05
Indeed, I started a thread about no breakage, now i have no audio or compositing. i think the devs answered my call :P
Checking for updates as i type......

---

### Post by ronacc on 2009-08-05
audio and compiz are both still working on my amd64x2/nvidia sys , the radio screenlet is causing python to take 100% of one core when I try to play it .

---

### Post by Regenweald on 2009-08-06
> **ronacc said:**
> audio and compiz are both still working on my amd64x2/nvidia sys , the radio screenlet is causing python to take 100% of one core when I try to play it .

I'm dead in the water with those two. I'll give it a couple days worth of updates and continue testing.
I've got a 64 bit system also, using the binary blob :)

---

### Post by ronacc on 2009-08-06
I'm using the repo 185.18.14 nvidia driver right now .

---

### Post by 3rdalbum on 2009-08-06
If you are using a non-repository driver, you will need to reinstall the driver after every kernel update and after most Xorg updates.

DKMS will handle this at kernel updates, if you set it up, but will not act on Xorg updates.

---

### Post by Regenweald on 2009-08-06
> **ronacc said:**
> I'm using the repo 185.18.14 nvidia driver right now .
I think that may be part of the problem, I'm using 190.16 against rc5. I'll wait it out though :P Without times like this you can't really appreciate a final release....

---

### Post by ronacc on 2009-08-06
I'm on the rc5 kernel but haven't gone to the 190 series driver yet maybe I'll give it a try tomorrow:P

---

