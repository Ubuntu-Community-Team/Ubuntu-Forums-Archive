---
title: "Kmplayer"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by asliyanage on 2009-12-25
can anyone tell me how to install Kmplayer with GUI interface to ubuntu 9.0?

---

### Post by tommcd on 2009-12-25
Why do you want to use KMplayer in Ubuntu? This will require you to install all the KDE libs and KDE base in your  Ubuntu Gnome  system. There is nothing inherently wrong with that though. When I use a Gnome system, I like to stick with Gnome and GTK apps, just to avoid the excess bloat that comes with managing a mixed Gnome GTK + Qt (KDE) system. Why add two engines to your car, when using just one will get you where you want to go?
You can just install MPlayer:
```
sudo apt-get install mplayer
```
If you don't like the GUI for MPlayer, then get SMplayer:
```
sudo apt-get install smplayer
```
SMplayer is quite nice. If you really want KMplayer then just:
```
sudo apt-get install kmplayer
```
If you need multimedia codecs, see:
[http://medibuntu.org/](http://medibuntu.org/)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Hope this helps.

---

### Post by x33a on 2009-12-25
@ tommcd,

smplayer also requires qt. though i must admit, it is the best frontend to mplayer.

---

### Post by asliyanage on 2009-12-25
can i have kmplayer with GUI in ubuntu 9.04?

---

### Post by SuperSonic4 on 2009-12-25
kmplayer is by definition a GUI program so yes.

Mplayer (the backend) is CLI unless explicitly said otherwise

---

### Post by asliyanage on 2009-12-25
can you  tell me how to install kmplayer with GUI to my ubuntu 9.04 ?

---

### Post by SuperSonic4 on 2009-12-25
Doesn't using apt-get work? ```
sudo apt-get install kmplayer
```

[http://kmplayer.kde.org/download.php](http://kmplayer.kde.org/download.php) - they say use the package manager's version although you can also compile

---

### Post by tommcd on 2009-12-25
> **x33a said:**
> @ tommcd,
smplayer also requires qt. though i must admit, it is the best frontend to mplayer.
Hmm, I did not know that. Thanks for pointing it out.
 I use SMplayer in Slackware, which includes Qt. But  SMplayer does not require all the KDE libs and KDE base that KMplayer would require, so it is less KDE dependent than KMplayer.
[http://www.linux.com/archive/feature/146958](http://www.linux.com/archive/feature/146958)
> SMPlayer is much better than Kaffeine for not being tied to KDE libraries dependencies. I wish many developers removed them as well on other programs where they're not absolutely necessary.

---

### Post by asliyanage on 2009-12-25
can you please tell me how to unstall kmplayer if i install it using 
sudo apt-get install kmplayer

---

### Post by SuperSonic4 on 2009-12-25
It will automatically install

to uninstall issue ```
sudo apt-get remove kmplayer
```

> **tommcd said:**
> Hmm, I did not know that. Thanks for pointing it out.
 I use SMplayer in Slackware, which includes Qt. But  SMplayer does not require all the KDE libs and KDE base that KMplayer would require, so it is less KDE dependent than KMplayer.
[http://www.linux.com/archive/feature/146958](http://www.linux.com/archive/feature/146958)

I didn't know that either although I always install the KDE libs and KDE base as part of KDE (obviously). I've found smplayer to be useful as a front-end to my svn compiled mplayer as it means I can pass the --disable-gui flag and just have smplayer

---

### Post by tommcd on 2009-12-25
> **asliyanage said:**
> can you  tell me how to install kmplayer with GUI to my ubuntu 9.04 ?
I already did in my first reply to this thread. KMplayer is in the Ubuntu 9.04 and 9.10 repos:
[http://packages.ubuntu.com/search?keywords=kmplayer&searchon=names&suite=jaunty&section=all](http://packages.ubuntu.com/search?keywords=kmplayer&searchon=names&suite=jaunty&section=all)
[http://packages.ubuntu.com/search?keywords=kmplayer&searchon=names&suite=karmic&section=all](http://packages.ubuntu.com/search?keywords=kmplayer&searchon=names&suite=karmic&section=all)
Make sure you have the proper repositories enabled:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by asliyanage on 2009-12-25
anyway where is the place this software going to installe?
normally in windows it goes to c:programm files/

---

### Post by x33a on 2009-12-25
it'll probably install to /usr/bin.

try
```
whereis <packagename>
```to find out, where it is installed.

---

