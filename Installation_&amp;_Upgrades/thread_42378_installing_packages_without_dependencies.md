---
title: "installing packages without dependencies?"
date: 2005-06-17
forum: Installation &amp; Upgrades
---

### Post by kerinin on 2005-06-17
my laptop is pretty slow, and i was wondering if it would speed things up to build my own packages (using apt-build or something similar) and to compile any dependancies into the binary.  

1) is it possible to do this and still have the ability to track packages with apt so i can upgrade or remove them easily

2) would this provide a performance boost?  i realize that it would require more disk space, but that's a penalty i'm willing to pay, especially for frequently used programs like firefox, openOffice, and my various media players.

thanks!

---

### Post by Alexander Kirillov on 2005-06-17
[QUOTE=kerinin]my laptop is pretty slow, and i was wondering if it would speed things up to build my own packages (using apt-build or something similar) and to compile any dependancies into the binary.  

1) is it possible to do this and still have the ability to track packages with apt so i can upgrade or remove them easily

2) would this provide a performance boost?  i realize that it would require more disk space, but that's a penalty i'm willing to pay, especially for frequently used programs like firefox, openOffice, and my various media players.

thanks![/QUOTE]
 I have no hard data, but AFAIK, on most apps it might give performance boost of under 5%. Hardly worth the trouble.

---

### Post by az on 2005-06-17
I think using shared vs static libraries gives much less improvement than that.  More like 0.5 percent, I think.

JDong would know....

---

### Post by kerinin on 2005-06-17
but what about startup times?  i realize i shouldn't need to start the programs very often but i have a nasty habit of closing windows i should just minimize, and i use enough programs i'd need about 10 desktops to really keep them organized.

---

### Post by jdong on 2005-06-17
Ok,

1: using apt-build will generate basically the same packages you see now, minus some architectural optimization. If your computer is on the slow side to begin with, you won't see ANY difference from -march/-mcpu optimization. Note that any packages that support -O1/-O2 optimization are already compiled optimized by the maintainers.

2: You can not install without dependencies, unless the dependencies are inside the program, in which case it'd be statically linked. Doing so is generally a bad idea, because it makes everything monstrous sized. Now, your hard drive is another bottleneck. And no, it wouldn't make anything faster.

3: There a general myth that started from Gentoo's USE flag system, that the less features you compile into your app, the faster it runs. Untrue. Maybe a LITTLE in the ways of load time, but it's not really gonna help you out.


So, no, your idea won't help you speed-wise. Now, some suggestions for speeding up your system:

1) Switch to lighter programs. Using GNOME? Try XFCE. Using Openoffice? See if AbiWord can suit most of your needs. Use the smaller apps most of the times, but when you need features from the bigger ones, get them. As far as browsing, I've found that the GNOME variety, like Epiphany and Galeon, are lighter than Firefox, even though it is the same browsing engine. Also, try Opera. No, it isn't open source, but it is great for older systems.

2) Try prelinking. It provides performance similar to static linking without all the side effects. Search the forums; I've written a Prelink howto, and I think there's another good one, too. It really speeds up Openoffice's start time.

3) As you've said yourself, if you keep the system on most of the times, don't close the programs you don't use. Minimize them or shove them onto another virtual desktop.

---

### Post by kerinin on 2005-06-17
i was using KDE to begin with  :-P 

i'm on XFCE now, and thinking about dropping to a openbox (or something similar) with a ROX desktop.

thanks for the prelinking suggestion, i'll look into it.

---

### Post by jdong on 2005-06-17
[QUOTE=kerinin]i was using KDE to begin with  :-P 

i'm on XFCE now, and thinking about dropping to a openbox (or something similar) with a ROX desktop.[/QUOTE]

Oh wow, then you'd get some serious speed improvements by dropping down to a lighter GUI. XFCE is probably as low as you can go without seriously sacrificing features of modern Linux desktops.

Unless you have a REALLY slow laptop, dropping down any further won't get you much of an improvement.

---

### Post by kerinin on 2005-06-17
it's a 433 pII.  xfce isn't bad at all, it's mostly that i've been enjoying playing with it...

---

### Post by jdong on 2005-06-17
ok, how much RAM are we talking about?

I've actually happily ran Kanotix (KDE HD-install) on that exact CPU speed, with 256MB RAM, with Openoffice and the works.

---

### Post by kerinin on 2005-06-17
256.  i can't really pin down what it is that's frustrating me about the speed - the internet is pretty slow, and it get hung up at strange times.  overall it just feels off.  that said, having moved to XFCE it's ceratinly much *better* 

for example, the javascript popup that came up to make that italic took about 10 seconds to close.  strange.

---

