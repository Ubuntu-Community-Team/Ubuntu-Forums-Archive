---
title: "Best Package Manager"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by Halfbrazilian on 2008-11-26
I have been using apt-get to install packages on my computer ever since I started using Ubuntu. A couple days ago I decided I wanted to try out the kde desktop so I did:

> sudo apt-get install kubuntu-desktop

It listed a bunch of packages it was going to have to install also and then installed them.

It did not take me long to figure out that I did not like kde. So, of course, I typed:

> sudo apt-get remove kubuntu-desktop

Unfortunately, it did not remove all the packages it installed. From my current understanding, it seems that kubuntu-desktop is a meta-package and when apt-get removes it, it does not remove all the programs installed with it.

So, this is my question:
What package manager should I use in order to avoid this in the future for other packages?

---

### Post by taurus on 2008-11-26
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Halfbrazilian on 2008-11-26
Thanks, I will use that to fix my current problem. The real question though is what package manager do I use to make sure that this does not happen again.

---

### Post by forkandles on 2008-11-26
Surely you have used Synaptic Package Manager? In my opinion it is the best GUI package manager there is.
If you prefer to use the terminal, I suggest you use aptitude instead of apt-get.
The differences are explained here.

[http://pthree.org/2007/08/12/aptitude-vs-apt-get/](http://pthree.org/2007/08/12/aptitude-vs-apt-get/)

Either use Synaptic to install aptitude or in terminal use
sudo apt-get install aptitude

---

