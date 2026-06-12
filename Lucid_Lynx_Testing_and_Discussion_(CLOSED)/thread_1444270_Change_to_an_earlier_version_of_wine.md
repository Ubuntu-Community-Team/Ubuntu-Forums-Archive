---
title: "Change to an earlier version of wine"
date: 2010-04-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by arnab_das on 2010-04-01
I'm currently using th latest version of wine (in the default repos) version 1.1.41

however most of the games dont run on this release. i'm comfy with something like 1.1.36. i have added the wine repos as well. however the synaptic isnt showing options to force (regress) ubuntu to install an earlier version. (btw the repos are of karmic since lucid repos arent available)

---

### Post by monraaf on 2010-04-01
You can download old jaunty debs from here.

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

AFAIK they still work with Lucid.

---

### Post by mc4man on 2010-04-01
you can get the .deb(s) you need from launchpad, for 64 bit install you probably only need 1, i386 you may need a couple more. (just get the same as you now have installed.

Stick the .deb(s) in an empty folder, cd to it and go 
```
sudo dpkg -i *.deb
```

the .36 builds
amd_64
[https://launchpad.net/ubuntu/+source/wine1.2/1.1.36-0ubuntu3/+build/1461412](https://launchpad.net/ubuntu/+source/wine1.2/1.1.36-0ubuntu3/+build/1461412)

i386
[https://launchpad.net/ubuntu/+source/wine1.2/1.1.36-0ubuntu3/+build/1461414](https://launchpad.net/ubuntu/+source/wine1.2/1.1.36-0ubuntu3/+build/1461414)

(if unsure ask first - someone can help I'm sure

---

### Post by arnab_das on 2010-04-01
> **mc4man said:**
> you can get the .deb(s) you need from launchpad, for 64 bit install you probably only need 1, i386 you may need a couple more. (just get the same as you now have installed.

Stick the .deb(s) in an empty folder, cd to it and go 
```
sudo dpkg -i *.deb
```

the .36 builds
amd_64
[https://launchpad.net/ubuntu/+source/wine1.2/1.1.36-0ubuntu3/+build/1461412](https://launchpad.net/ubuntu/+source/wine1.2/1.1.36-0ubuntu3/+build/1461412)

i386
[https://launchpad.net/ubuntu/+source/wine1.2/1.1.36-0ubuntu3/+build/1461414](https://launchpad.net/ubuntu/+source/wine1.2/1.1.36-0ubuntu3/+build/1461414)

(if unsure ask first - someone can help I'm sure

thanks mate. it worked! unfortunately somehow some games which worked on 9.10 on 1.1.36 isnt working on 10.04. strange.

but anyway, most games are working, so thanks a lot mate.

---

