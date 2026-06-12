---
title: "Installing KDE changes boot screen"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by aquaboogie on 2007-04-24
Hello. After installing Feisty Fawn I installed kubuntu-desktop and now the startup screen shows the kubuntu graphic. Any way I can get it to say Ubuntu again?

Thanks.

EDIT: Also, the Epiphany start page is now the Kubuntu welcome page. (?)

---

### Post by sblanzio on 2007-04-25
same here please at least tell us a useful link!!
tnx

EDIT:
trying this one:
[http://ubuntuforums.org/showthread.php?t=323520&highlight=usplash](http://ubuntuforums.org/showthread.php?t=323520&highlight=usplash)

i'll let you know if this worked (the previous didnt)

---

### Post by sblanzio on 2007-04-25
the link above worked perfectly!
in particular, i used these lines:

> 

1. I had to run this:
```
cd /usr/lib/usplash
```
to get to the usplash directory.

2. Then I ran
```
sudo ln -sf usplash-theme-ubuntu.so usplash-artwork.so
```
to manual establish the bad link from the theme to usplash artwork.

3. I then reran:
```
sudo update-alternatives --config usplash-artwork.so
```
and selected my ubuntu usplash theme to ensure that, using the link that I had manually set before, usplash would use the selection that I wanted out of the alternatives list.



hth!
bye

---

### Post by aquaboogie on 2007-04-26
Thanks so much for your help. This worked perfectly. :)

---

