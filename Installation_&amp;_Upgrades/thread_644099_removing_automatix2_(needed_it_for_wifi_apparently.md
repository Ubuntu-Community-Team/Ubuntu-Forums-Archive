---
title: "removing automatix2? (needed it for wifi apparently...)"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by drazgoth on 2007-12-18
H'lo!

I just started using linux and it wouldn't recognize my network card, so I followed this guide to get it working: [http://dhashi.wordpress.com/2007/06/10/ubuntu-704-on-a-dell-inspiron-710m/](http://dhashi.wordpress.com/2007/06/10/ubuntu-704-on-a-dell-inspiron-710m/)

which requires me to use automatix2...

of course now any time I try to install other programs I get a conflict warning or something, I browsed through the forums a bit and pretty much it seems like a lot of people would have said don't install automatix at all costs...  So on to my question...

What do I do now? :D

Is there a way to remove it, or do I have to reinstall linux or something?  Thanks!

---

### Post by taurus on 2007-12-18
You need to edit /etc/apt/sources.list and remove all the entries that automatix added in.

```
gksudo gedit /etc/apt/sources.list
```
Save it.  Then, run

```
sudo apt-get remove automatix2
sudo apt-get update
```

---

