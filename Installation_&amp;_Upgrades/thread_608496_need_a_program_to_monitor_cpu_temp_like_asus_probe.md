---
title: "need a program to monitor cpu temp like asus probe"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by ayet on 2007-11-10
Is there anything like this in Ubuntu

---

### Post by forestpixie on 2007-11-10
you need to install sensors 
```
sudo apt-get install lm-sensors
```

then run sensors-detect
```
sudo sensors-detect
```

then you can either use ```
sensor
``` in a terminal if you just want to look now and again, I use x-sensors which is in the repos - which runs from the system tools menu
```
sudo apt-get install xsensors
```
or you could get one of the gdesklets 
```
sudo apt-get install gdesklets
```
which would do the job - gets put in accessories, also there's something called conky - which goes on your desktop - looked once didn't like it so can't say much about that
```
sudo apt-get install conky
```

---

### Post by billmilosz on 2007-11-12
Doesn't work in Ubuntu 7.10 / AMD64

---

### Post by FredWst on 2007-11-12
Hi

Try sensors-applet witch provide temperatures in gnome taskbar.

sudo apt-get install sensors-applet.

And right clic in taskbar then "add applet" choose hardware monitor.

Fred

---

### Post by erfahren on 2007-11-12
I use "computertemp" out of the repos

---

### Post by svtfmook on 2007-11-12
> **billmilosz said:**
> Doesn't work in Ubuntu 7.10 / AMD64
for conky, you have to grep it from the conf file.

```

sudo apt-get install gkrellm

```

easiest way right there.  gdeklets are horrible and ugly.  gkrellm is skinnable without having to revamp a configuration file.

---

