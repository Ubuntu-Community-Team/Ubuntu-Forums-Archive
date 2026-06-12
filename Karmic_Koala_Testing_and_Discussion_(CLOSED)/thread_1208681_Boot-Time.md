---
title: "Boot-Time"
date: 2009-07-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by josedb on 2009-07-09
Iam using 9.10 version, and this is the output for bootchar, question is, Is it ok? i see so many udev and devkit-disks-pa


[[IMG]http://img509.imageshack.us/img509/366/joselaptopkarmic2009070.png[/IMG]](http://img509.imageshack.us/my.php?image=joselaptopkarmic2009070.png)

---

### Post by budluva04 on 2009-07-09
0:19 is great, your good don't worry mine is the same, in fact i get a 0:19 boot aswell :P

---

### Post by tad1073 on 2009-07-09
50 sec. from pushing the poower to usable system

---

### Post by tjeremiah on 2009-07-09
How does one display their boottime? Mines is probably the slowest since I used wubi..

---

### Post by taavikko on 2009-07-09
> **tjeremiah said:**
> How does one display their boottime? Mines is probably the slowest since I used wubi..

Install "bootchart" It generates an .png image of startup.
It will be located in /var/log/bootchart/

---

### Post by wayne_cat on 2009-07-09
almost 27 seconds on a 3 year old Apple Macbook Pro - 2.0 GHz Core Duo

I don't have so many devkit-disks-pa processes ... system has only one disk.


...

---

### Post by taavikko on 2009-07-09
Hmm.. something funny here, since it has used to be around ~14s for me

---

### Post by davideotape on 2009-07-09
Bah, I'm around 50 secs on a 10 year old hard drive with 2GB ram and 1.86Ghz dual core. Running boinc doesn't help a great deal though, and I've found that readahead takes up quite a bit of CPU.

---

### Post by keith.newell on 2009-07-09
Sweet!  0:14 on my dell mini 9  :)

---

### Post by MacUntu on 2009-07-09
* Fresh and untweaked installation
* Core Duo T2400 (1.83GHz)
* 2GB RAM
* 7200rpm 320GB HDD
-> 26 seconds from GRUB2 to an usable desktop 
-> [http://img.xrmb2.net/images/963273.png](http://img.xrmb2.net/images/963273.png)

IIRC jaunty was faster.

---

### Post by inportb on 2009-07-11
I get 19 seconds... pretty good. Except there's a cr@pload of processes :p

---

### Post by philinux on 2009-07-11
> **taavikko said:**
> Hmm.. something funny here, since it has used to be around ~14s for me

Yep same here 20 secs. Why is there a 4/5 second delay before anything happens. I'd sure like to shave 5 seconds off.

---

### Post by taavikko on 2009-07-11
> **philinux said:**
> Yep same here 20 secs. Why is there a 4/5 second delay before anything happens. I'd sure like to shave 5 seconds off.

This indeed is peculiar, since my laptop doesn't have this delay. All free drivers.
Main machine has this delay, with nvidia's binary blob.

But let's give this some time. FF is still ahead and after that we should begin to see some real changes to the system...

---

