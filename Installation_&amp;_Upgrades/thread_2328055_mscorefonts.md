---
title: "mscorefonts"
date: 2016-06-16
forum: Installation &amp; Upgrades
---

### Post by CliffordHoward on 2016-06-16
I know this has been posted hundreds of times, but I am still experiencing this problem after following advice from other threads.

[http://ubuntuforums.org/showthread.php?t=2179342](http://ubuntuforums.org/showthread.php?t=2179342)

That thread specifically.

```
$ sudo apt-get clean
$ sudo apt-get install --reinstall ttf-mscorefonts-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ttf-mscorefonts-installer needs to be reinstalled, but I can't find an archive for it.


```

No matter what I do, that's what happens.
Nothing will solve it.
I'm brand new to Ubuntu and only switched because windows 10 crashed and I could not get a fix for it. Nothing would work.
So if anyone would like to personally help me out with getting started and getting this cleared up, I would appreciate it very much.

---

### Post by howefield on 2016-06-17
Does..

```
sudo dpkg --configure -a
```

provide any output ?

---

### Post by Impavidus on 2016-06-17
Is the multiverse repository enabled? Go to software sources/package sources/software & updates (the exact name varies a bit) &#8594; Ubuntu software tab &#8594; make sure multiverse is enabled.

Which version of Ubuntu have you installed?

---

