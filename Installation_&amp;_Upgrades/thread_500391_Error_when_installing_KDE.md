---
title: "Error when installing KDE"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by denny14 on 2007-07-13
Hi.
1) I downloaded the separate files for KDE rather than installing it straight from the internet. I went to [www.kde.org/download](www.kde.org/download) and downloaded about 19 files from that site. I've extracted the .tar.bz2 files and now I'm up to the ./configure stage. When I go ./configure, it comes up with an error after about 1 minute of configuring it. The error says: 
checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!
What on earth does that mean???
2) Once I do the ./configure stage, I have to type 'make' in the Terminal. Do I type make for each separate package or do I do them all at once?
3) Do I need to use Konstruct or not?
Thanks :)

---

### Post by yabbadabbadont on 2007-07-13
You would be better off just running in a terminal window ```
sudo apt-get install kde-core
```

---

### Post by Kralizec on 2007-07-13
I'm still relatively new to Ubuntu, but I'll try to help since there are no other replies so far...

1) This means you're missing a dependency of the package you're trying to configure. Basically what that boils down to is that something the package you're installing needs isn't available (in this case, the X libraries). The suggestion I can make is that you go into synaptic and search for "X libraries" and mark things that sound like they may be right for installation (one's I'd try are xorg, xorg-dev, xutils-dev, xlibs-dev, x11-common). 
Thats what I usually do when I get a configuration error.

2) I believe you have to type make for each package you've configured. Every ./configure needs to be paired with a 'make' and a 'make install' (or 'sudo make install').

3) Can't help there, not sure what Konstruct is.

---

