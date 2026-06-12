---
title: "trouble installing ubuntu from alternative cd"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by compuwiz12 on 2007-04-26
i'm running a 933mhz 128mb computer and i'm trying to istalll ubuntu on it.  I put in the cd and hit enter on the default option which is istall in text mode. It then goes to a blank screen with the blinking _ so you can type stuff and nothing happens.  What am I doing wrong?

---

### Post by zvacet on 2007-04-26
[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

If this gives you no result maybe you can try replace ubuntu desktop with xubuntu because you are low in RAM and xubuntu is lighter.

```
sudo aptitude remove ubuntu-desktop
```

```
sudo aptitude install xubuntu-desktop
```

---

### Post by compuwiz12 on 2007-04-26
yeah i tried that but it gives two errors while loading:

1.   [   234.657157] I/O error on device fd0 logical block 0

2.   [   369.2287957]  Yenta: no bus associated with 0000:01:0c.o! (try'puizassign=busses')


then :confused:  loads with the little bar bouncing then gos to a blank blue screen
also i have windows 2000 pro on there could that be affecting anything?

---

