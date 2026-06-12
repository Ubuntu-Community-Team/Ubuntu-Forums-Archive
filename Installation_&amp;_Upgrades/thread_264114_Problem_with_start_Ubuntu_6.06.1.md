---
title: "Problem with start Ubuntu 6.06.1"
date: 2006-09-24
forum: Installation &amp; Upgrades
---

### Post by amxcs on 2006-09-24
I install success.
After restart :
[[IMG]http://img209.imageshack.us/img209/895/sunp0037fq0.jpg[/IMG]](http://imageshack.us)
[B]Loading Essential Drivers :                 [OK]
Mounting Root File System :                blank
Waiting for root filesystem :              blank[/B]

After 3-4 min.:
[[IMG]http://img209.imageshack.us/img209/6751/sunp0041xk2.jpg[/IMG]](http://imageshack.us)
How to fix it?
I'm Bulgarian.

---

### Post by angkor on 2006-09-24
You are trying to boot ubuntu from a partition that doesn't exist. On what partition did you install ubuntu?

---

### Post by johny00 on 2006-09-24
Hi guys, amxcs is my friend, we try to install ubuntu so many times, but nothing, the same error
```
Loading Essential Drivers : [OK]
Mounting Root File System : blank
Waiting for root filesystem : blank

```
We install ubuntu on ex3 partition, and swap partition. First on the machine, we have windows xp, with parition magic we create those partitions, and try to install, but after restart..

We try to format the entire hard drive, but the same error.

---

### Post by amxcs on 2006-09-24
Please help !!!

---

### Post by Henry Rayker on 2006-09-24
it looks like you are booting from hda7 which does not exist, apparently. Which partition did you install Ubuntu on? What is its name?

---

### Post by amxcs on 2006-09-24
hda7 !

---

### Post by amxcs on 2006-09-24
How to fit it ?

---

