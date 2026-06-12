---
title: "Repartitioning HardDrive"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by TJ1234 on 2008-01-30
Hello, I'm currently dual-booting WinXP and Ubuntu. XP is my main OS that I use every day and I would like to give it a bit more space on the partition than Ubuntu. However I cannot seem to make the GParted Partition Editor work from Ubuntu. Any help would be appreciated thanks.

---

### Post by taurus on 2008-01-30
You need to do that from a LiveCD because you cannot resize a partition while you are using it.  Use GParted LiveCD for it.

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

p.s.  _ALWAYS_ back up your important files in case something goes wrong.

---

### Post by TJ1234 on 2008-01-30
Ok thanks.. That was pretty much the answer I was looking for.

---

### Post by TJ1234 on 2008-01-30
I've made the gparted live CD and it boots and everything is ok but then it just stops and says in a square red box in the middle of the screen. It gives me this:

NO SUPPORTED MODE
H: 75.0 KHz
V: 60.0 KHz

How do I get past this?

---

### Post by zvacet on 2008-01-31
I think one of first things you see in Gparted is force....driver and there you select wich one you want.I belive you can not be wrong if you select vesa.

---

### Post by TJ1234 on 2008-01-31
Hmm.. Ok, it got a bit further that time. However, now it gets to a phase where it attempts to check my hardware, it finds my processor then nothing. I let it run for an additional ten minutes but nothing else came up. Any ideas on what to do from here?

---

### Post by zvacet on 2008-01-31
If you know wich driver you use try again with it instead of vesa.That is all I can think of,because I never has problems booting Gparted.

---

### Post by TJ1234 on 2008-01-31
I don't know which driver I use. How would I find that out?

---

### Post by zvacet on 2008-01-31
```
lshw
```

---

