---
title: "can not install"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by nacho1 on 2008-02-06
I tried installing UBUNTU 7.10 on IBM NetVista MT-M 8303-42U it just hangs on a beige screen and after about 1 hour i get UBUNTU desktop and 2 folders(samples, desktop) but does not install. I'm not familiar with pc's. Any help appreciated.

---

### Post by taurus on 2008-02-06
What is the spec of that IBM machine?  Sounds like it's a old with lower RAM.

If you have  256MB of RAM or less, you should consider using the alternate CD to install it or even try the alternate CD of Xubuntu.

[http://www.xubuntu.org](http://www.xubuntu.org)

---

### Post by nacho1 on 2008-02-06
Yes it has 256 mg of ram, pentium 4, 2.4ghz. Tried Xubuntu got further along but same thing, just hangs, cursor and keyboard erratic and never finished install.

---

### Post by zvacet on 2008-02-07
Chek [md5sum](https://help.ubuntu.com/community/HowToMD5SUM) and chek disc for errors.Secon option is to download Xubuntu alternateCD.

---

### Post by Carl H on 2008-02-07
> **nacho1 said:**
> I tried installing UBUNTU 7.10 on IBM NetVista MT-M 8303-42U it just hangs on a beige screen and after about 1 hour i get UBUNTU desktop and 2 folders(samples, desktop) but does not install. I'm not familiar with pc's. Any help appreciated.

That sounds like you've booted a Live CD. You need to select the 'install' option once the desktop has appeared. But if it's taking an hour (should be a few minutes max), then the alternate CD is definitely the way to go.

---

### Post by nacho1 on 2008-02-07
Thank you, installed Xubuntu successfully but have a no network - no network devices have been found, icon / mesage on the upper right hand corner, when i choose the set up manually it only gives me the option for dial up. I have everything connected to a cable modem. Any suggestions?

---

### Post by zvacet on 2008-02-08
**Programs<accessories>terminal**

```
pppoeconf
```

to see will Ubuntu recognize your network card

---

