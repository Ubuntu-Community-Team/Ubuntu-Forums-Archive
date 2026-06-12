---
title: "How to Burn Ubuntu DVD Iso"
date: 2006-04-20
forum: Installation &amp; Upgrades
---

### Post by rEvolution27 on 2006-04-20
Hello all,
I'm new to ubuntu and linux on the whole. I downloaded the DVD combo (live-dvd + install) of ubuntu 5.1 for the AMD 64-bit achitecture but when i try to burn it (with Nero) i get an error saying the file is over 2gigs and can't be burned as an iso. I thought it could fit on one dvd.... 

Is there any way of compressing it? or separating it onto multiple dvd's? or is Nero the problem? 
I'm using windows XP and my dvd is supposed to have a capacity of 4.7gigs. 

.. i also downloaded and ISO recorder but that only seems to do CDs. 

Thanks in advance.

---

### Post by cleverselfreferentialname on 2006-04-20
Nero can be moronic like that. Your DVDs are almost certainly of such a capacity. Here, try a different app [http://cdrdao.sourceforge.net/](http://cdrdao.sourceforge.net/)

---

### Post by rEvolution27 on 2006-04-20
[QUOTE=cleverselfreferentialname]Nero can be moronic like that. Your DVDs are almost certainly of such a capacity. Here, try a different app [http://cdrdao.sourceforge.net/](http://cdrdao.sourceforge.net/)[/QUOTE]

Thanks for the reply. I will try.

---

### Post by Topsiho on 2006-04-21
Download and install K3b. It's a KDE program but in Gnome you can install KDE-applications too, most easy with  (for k3b, in a terminal):

sudo apt-get install k3b

In minutes you have K3b with which you can burn DVD-images, see in menu Applications (or: Hulpmiddelen if you are Dutch :) )

I do not think that K3B has a 2GB-limit but I can not guarantee that.

Topsiho

---

### Post by Topsiho on 2006-04-21
If you have not Ubuntu installed yet, you could download and burn a Knoppix .iso image and use K3b that you'll find there.

Good luck,

Topsiho

---

### Post by helmet on 2006-04-24
[QUOTE=rEvolution27]Hello all,
I'm new to ubuntu and linux on the whole. I downloaded the DVD combo (live-dvd + install) of ubuntu 5.1 for the AMD 64-bit achitecture but when i try to burn it (with Nero) i get an error saying the file is over 2gigs and can't be burned as an iso. I thought it could fit on one dvd.... 

Is there any way of compressing it? or separating it onto multiple dvd's? or is Nero the problem? 
I'm using windows XP and my dvd is supposed to have a capacity of 4.7gigs. 

.. i also downloaded and ISO recorder but that only seems to do CDs. 

Thanks in advance.[/QUOTE]

i'm guessing what you did was try to burn the file as a data file, not as an image. you probably opened up nero and added the downloaded iso and tried to burn it like that, but you were in iso burning mode, which is how the dvd will be burned, and it can't do files over 2 gigs. you need to open up nero (not nero express) and go to "Recorder -> Burn Image" and select the downloaded file that way.

---

