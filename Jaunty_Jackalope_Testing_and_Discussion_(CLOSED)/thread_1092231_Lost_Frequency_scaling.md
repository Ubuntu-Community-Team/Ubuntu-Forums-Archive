---
title: "Lost Frequency scaling"
date: 2009-03-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by plun on 2009-03-10
Full speed without scaling today.....  (Intel 5200 dual core) 

Error message from the scaling applet.


Anyone else with this challenge ?

---

### Post by ronacc on 2009-03-10
scaling ok on my amd64x2 sys . uptodate as of this morning .

---

### Post by taavikko on 2009-03-10
Working here also:

model name	: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz
```
cat /proc/cpuinfo |grep -i "cpu Mhz"
cpu MHz		: 1600.000
cpu MHz		: 1600.000
cpu MHz		: 1600.000
cpu MHz		: 1600.000
cpu MHz		: 1600.000
cpu MHz		: 1600.000
cpu MHz		: 1600.000
cpu MHz		: 1600.000

```

Running bit high though...

Might as well add, that haven't changed anything after installation,
So pretty vanilla flavor here :)

---

### Post by plun on 2009-03-10
Well... this one just came this morning...

[IMG]http://ubuntu-pics.de/bild/10779/snapshot22_7fNKug.png[/IMG]


I can also see with the sensors values and **vCore** that its full speed.

EDIT
plun@plun:~/do$ cat /proc/cpuinfo |grep -i "cpu Mhz"
cpu MHz		: 2812.401
cpu MHz		: 2812.401

100%.....slightly overclocked

---

### Post by plun on 2009-03-10
Followup....

It seems to be this bug and update....

[https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/331044](https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/331044)

---

### Post by plun on 2009-03-10
Solved with kernel 2.6.28-9, case closed  

Something broke with RC7 and latest updates....;)


plun@plun:~$ cat /proc/cpuinfo |grep -i "cpu Mhz"
cpu MHz        : 1200.000
cpu MHz        : 1200.000

---

### Post by ronacc on 2009-03-10
I'm on the .29-rc kermel thats probably why I missed that one :D

---

