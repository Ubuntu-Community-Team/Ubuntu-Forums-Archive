---
title: "how do I install xubuntu"
date: 2006-05-11
forum: Installation &amp; Upgrades
---

### Post by johnathan on 2006-05-11
I realized that the default installation won't run on my computer due to insufficient memory, so therefore I may have to install xubuntu on my computer.. 

The only problem is how to install it...

I was wondering if anyone could tell me how to install the xubuntu desktop.....

Thank you!!!

---

### Post by confused57 on 2006-05-11
This is probably the most lightweight way to install Xubuntu:

[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

---

### Post by aysiu on 2006-05-11
Follow these directions:
[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

---

### Post by Stewart on 2006-05-11
You could download the Xubuntu cd.

[http://cdimage.ubuntu.com/xubuntu/](http://cdimage.ubuntu.com/xubuntu/)

Stewart

---

### Post by jtibau on 2006-05-12
you may just do "sudo apt-get install xubuntu-desktop" since you already have a working (albeit slow) OS, it doesn't seem like you should install again, just add the packages :)

---

### Post by Geoneil on 2006-05-12
Xubuntu has its own [website](http://www.xubuntu.org/)

Although there doesn't appear to be much there as yet (download link?) probably with it being so new...

I have XFCE on my PC as well as Gnome and KDE, not a bad desktop, actually quite a good desktop, I like it better than Gnome truth be told and sometimes go in there instead of KDE.  (I've pretty much always used KDE-based distros and I actually have Kubuntu)

---

### Post by johnathan on 2006-05-15
Tried everything......
It comes up as unable to locate xubuntu packages or something like that.....

Any other suggestions.....

Thanks

---

### Post by aysiu on 2006-05-15
[QUOTE=johnathan]Tried everything......
It comes up as unable to locate xubuntu packages or something like that.....

Any other suggestions.....

Thanks[/QUOTE] Copy and paste these commands into the terminal: ```
wget -c http://www.psychocats.net/ubuntu/breezy.list
sudo mv /etc/apt/sources.list /etc/apt/sources_old.list
sudo mv breezy.list /etc/apt/sources.list
sudo aptitude update
sudo aptitude install xubuntu-desktop
```

---

### Post by johnathan on 2006-05-16
It came as temporary failure in name resolution..... It also said at the bottom finished downloaded 0 bytes in 0 files....

Would that be a bad thing?

---

### Post by aysiu on 2006-05-16
Can you paste the exact output?

---

### Post by johnathan on 2006-05-16
[QUOTE=aysiu]Can you paste the exact output?[/QUOTE]

No!

I am at the command prompt like black and white screen

---

### Post by aysiu on 2006-05-16
There are only two times I could track down that "temporary failure in name resolution" error:

[http://www.ubuntuforums.org/showthread.php?t=173386](http://www.ubuntuforums.org/showthread.php?t=173386)
[http://www.linuxforums.org/forum/linux-newbie/7489-apt-yum-wont-work.html](http://www.linuxforums.org/forum/linux-newbie/7489-apt-yum-wont-work.html)

Both times, it had to do with someone using a proxy for internet. Take a look at those two threads. They may help.

---

### Post by johnathan on 2006-05-16
Is there a way I can install xubuntu off the ubuntu install cd......

---

### Post by aysiu on 2006-05-16
[QUOTE=johnathan]Is there a way I can install xubuntu off the ubuntu install cd......[/QUOTE] No. You need either the Xubuntu install CD (Dapper only) or to install it off the internet.

---

