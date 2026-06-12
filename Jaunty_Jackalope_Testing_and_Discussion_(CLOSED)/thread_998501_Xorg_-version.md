---
title: "Xorg -version"
date: 2008-11-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by shirishagarwal on 2008-11-30
Just for self 
 How do I find which xorg-xserver version I am running. One of the ways is obviously doing 

```

$ less /var/log/Xorg.0.log 

```

A much more better way 

```

$ Xorg -version 

```

---

### Post by plun on 2008-12-01
More important... what graphic card and driver do you use ?

Fail safe mode should just work.

---

### Post by anhvu2875 on 2008-12-01
**plun**
Jaunty sill gets error with Intel VGA card ? :(:(

---

### Post by uBeer on 2008-12-01
I don't think there's a problem: it's just a note to self... :)

---

### Post by DougieFresh4U on 2008-12-01
Why is machine using 'vesa'  (xorg log shows)instead of my 'Intel865G' onboard graphics? Where and how to change and will changing 'bork' machine as it did 4 weeks ago?

---

