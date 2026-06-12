---
title: "Is there a certain folder that programs are installed too?"
date: 2007-01-01
forum: Installation &amp; Upgrades
---

### Post by bobleny on 2007-01-01
Is there a certain folder that programs are installed too? Say, I just downloaded firefox, from mozilla.org and I need to extrat the .tar.gz somewhere right?

Where would a program like this go in my HDD?

---

### Post by kidders on 2007-01-01
Hi there,

It would be better to use the version provided in the package repositories, imo. In any case, what to do with a downloaded archive really depends on what's in it.

---

### Post by bobleny on 2007-01-01
> **kidders said:**
> It would be better to use the version provided in the package repositories, imo. 
What you mean by repositories and imo?

> **kidders said:**
> In any case, what to do with a downloaded archive really depends on what's in it.

How do I determine where it should go?

---

### Post by kidders on 2007-01-01
> **bobleny said:**
> What you mean by repositories and imo?
Most Linux distros provide very large collections of software, specifically tailored to work well with them. Ubuntu is no different.

> **bobleny said:**
> How do I determine where it should go?
That depends on what's in the archive.

---

### Post by bobleny on 2007-01-01
Well, I would like to have firefox. How do I get it? Is it already installed with Ubuntu? I looked in the adapt manager thingy, but I don't under stand what all the differences are in the packages... Is that how I am supposed to get firefox?

I feel lost :(

---

### Post by kidders on 2007-01-01
Yep :-) Check out some of the online documentation and HOWTOs on installing software with Ubuntu/Debian.

---

### Post by sloggerkhan on 2007-01-01
IMO= in my opinion

Reporitories are places your computer can automatically install software from. They are sorta remote storage rooms for software designed to work with your OS.

To see which ones you have active: System > Administration > Software Sources

To install new programs the easiest way: Applications > Add Remove

To install new stuff and all kinds of things: System > Administration > Synaptic Package Manager

Similar to Synaptic but on the command line: sudo aptitude

There are a number of official repositories and depending on your ideological leanings, you may wish to make differing numbers of them active.

In any case, there are many reasons you might want a piece of software not in the repos or install your own latest version of something. What you do depends on the file type. In the best case, you download the file, double click on it, and hit install package. In other scenerios, you have to move stuff manually or compile from source. (Lots of people like to compile from source because they want an "optimized" system and nothing is optimized like something compiled by the hardware it runs on, I guess.)

---

### Post by sloggerkhan on 2007-01-01
oh, and to tell if you have firefox: applications > internet > firefox is the default menu path for it on a new install.

---

### Post by bobleny on 2007-01-01
Yay! I got Firefox! thanks you!

No more Konquerorer thingy mabober

---

### Post by sloggerkhan on 2007-01-01
You should specify that you use kubuntu and not ubuntu when you have this sort of question... I assumed you were using ubuntu under gnome.

---

### Post by bobleny on 2007-01-01
This Synaptic Package Manager thing you mentioned, is there something like that in KDE?

---

### Post by sloggerkhan on 2007-01-01
yes, there is. I don't use KDE because it tends to annoy me, but I think it has synaptic, just not in the same menu location as in gnome. (don't quote me on that.)

---

### Post by aysiu on 2007-01-01
I think you should check out these two links.

This script will help you install the newest Firefox (the Mozilla build, not the Ubuntu one):
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

That is a non-typical software installation. If you want to understand *typical* software installations, read this. It will explain all this mumbo-jumbo about repositories.
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

