---
title: "installing just a single package from breezy?"
date: 2005-07-25
forum: Installation &amp; Upgrades
---

### Post by cage on 2005-07-25
Hello!

I want to install just a single package of breezy, namely it's gnome-applets.
Is that possible at all? Or do you have to fulfill a lot of dependencies then?

I want to do this because I need a feature of one applet that has been added after the release of gnome 2.10 and hoary. And I was told that I could use the version of breezy.
But I don't know where to download it (the single .deb-package) nor am I sure if s.th. like the pining-thing (I think it's also possible with ubuntu, isn't it?) makes sense in this case.

Thanks for your help in advance!

Carsten

---

### Post by heimo on 2005-07-25
For just one application, I'd just try downloading deb-packages
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gnome-applets&searchon=names&subword=1&version=breezy&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gnome-applets&searchon=names&subword=1&version=breezy&release=all")

gnome-applets and gnome-applets-data and then installing using dpkg
 ```
dpkg -i packagename.deb

``` 

It may work. That'll show you if there are unmet dependencies and you could try solving those manually or learn about pinning.
[http://jaqque.sbih.org/kplug/apt-pinning.html]("http://jaqque.sbih.org/kplug/apt-pinning.html")

EDIT2:
[https://wiki.ubuntu.com/PinningHowto](https://wiki.ubuntu.com/PinningHowto)


EDIT: Of course, this needs disclaimers - there's a good chance you'll "bork" your installation, mixing hoary and breezy can cause unexpected things to happen (your son will become alcoholic and moon will crash earth)

---

### Post by cage on 2005-07-26
Thanks for this link.

I downloaded it and tried to install, but then I will have to install a lot of new libraries out of the breezy-branch. At the moment I don't want to do this, because I think it's a bit too risky. 

Anyway thanks a lot, perhaps I will give it another try sometimes.

Greetings,
Carsten

---

### Post by az on 2005-07-26
You are going to have to install all of the dependancies, as well.

The thing is, that does not mean that you need to upgrade your whole system to breezy, just that subset of packages.

---

### Post by cage on 2005-07-27
Yes of course. but now I prefer to wait until breezy is officially released.

Anyway, thanks!

---

