---
title: "Medibuntu repository link for Intrepid Ibex??"
date: 2008-07-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Robertjm on 2008-07-19
Hi all,

Upgraded to Intrepid Ibex and am working the kinks out of my system. So far, so good. However, I need to know whether there is a medibuntu repository for Intrepid Ibex yet?

Yes, I realize its in Alpha right now! If there is no Intrepid repo yet, can I use the one for Hardy?

Thanks!!

Robert

---

### Post by mc4man on 2008-07-19
I believe some people are using hardy's repo. i got what I needed from here with direct downloads only. The testing packages matched up well.
[http://debian-multimedia.org/pool/main/](http://debian-multimedia.org/pool/main/)

somewhat related thread
[http://ubuntuforums.org/showthread.php?t=858758](http://ubuntuforums.org/showthread.php?t=858758)

---

### Post by Robertjm on 2008-07-20
I ended up adding the medibuntu repo for Hardy, figuring the packages I wanted to add haven't changed in quite awhile.

After adding them things seem to be working just fine!!

Robert

---

### Post by Saint Angeles on 2008-10-21
try this command:

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by OrangeCrate on 2008-10-21
<deleted>

Just saw that this is an old thread.

Edit:

For anyone else reading this, and you need the Intrepid info, it can be found here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

