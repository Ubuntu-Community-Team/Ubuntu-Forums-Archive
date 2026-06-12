---
title: "Fresh install - reinstall all previously installed packages"
date: 2014-01-13
forum: Installation &amp; Upgrades
---

### Post by irvingdave1 on 2014-01-13
Hi,

I'm going to perform a complete fresh install of ubuntu - and I'd like to work out how best to get things 'back to how they were' (or near enough ;) ).
So, I'll be taking a back-up of /etc - and can presumably apply back config changes for apache2, postfix, etc following install.
Before that though, I'll need to apt-get install all the stuff I have on my current installation. Are there any easy ways to prepare for this? (E.g. get full package list saved somewhere so I can have a script re-install my stuff?).

There is probably other stuff I'll need that I haven't thought of: Wondering if there are any guides for this sort of situation? (Couldn't find much)

Many thanks in advance,

Dave

---

### Post by steeldriver on 2014-01-13
Have a look at dpkg --get-selections / dpkg --set-selections

---

### Post by ibjsb4 on 2014-01-13
You can also use [Synaptic Package Manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=markings+list+synaptic&sa=Search&cof=FORID:9") and create a markings list.

In terminal:
```

sudo apt-get install synaptic
```

Edit:

[http://ubuntuforums.org/showthread.php?t=2147845](http://ubuntuforums.org/showthread.php?t=2147845)

[http://ubuntuforums.org/showthread.php?t=1748541&p=10765330#post10765330](http://ubuntuforums.org/showthread.php?t=1748541&p=10765330#post10765330)

---

### Post by irvingdave1 on 2014-01-13
Will take a look at both. Thanks very much!

---

