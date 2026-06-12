---
title: "Unable to download, because I can't find gdebi-gtk"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by robot952 on 2014-04-18
Help! I Can not find gdebi-gtk. I was trying to download Wine, using Ubuntu Software center to download won't do the trick, but I heard gdebi-gtk will.  I installed Synaptic pckge manager, is that why I can't find it? Is there a way to install it now without reinstalling Ubuntu?  Thx.

---

### Post by kc1di on 2014-04-18
Hi robot952,

I'm not exactly sure what your trying to do gdebi has nothing to do with wine.  and it can be installed from the repositories. but the correct name is not gdebi-gtk it's just gdebi - do a search for gdebi in synaptic and you'll find it.  You should also be able to install wine by doing a search for wine in Synaptic too. 
Make sure you have an internet connection and all should work well. 

You could also do it from the terminal with the following commands:
```
sudo apt-get update
```
```
sudo apt-get install wine 
```
and if you want gdebi which is a handy tool to have but not essential, enter
```
sudo apt-get install gdebi 
```

---

### Post by robot952 on 2014-04-18
Thx Kc!

---

### Post by kc1di on 2014-04-18
Your Welcome hope it works for you ;)

---

### Post by robot952 on 2014-04-18
By the way, it installed, but when I go to dash home, and rt click applications I see only 'winetricks' not 'wine'.  Any idea why that is?

---

### Post by kc1di on 2014-04-18
> **robot952 said:**
> By the way, it installed, but when I go to dash home, and rt click applications I see only 'winetricks' not 'wine'.  Any idea why that is?

you should see wine wineconfig and notepad and uninstall wine software.  make sure under filters applications is highlighted.

---

