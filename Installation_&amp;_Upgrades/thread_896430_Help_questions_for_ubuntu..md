---
title: "Help questions for ubuntu."
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by jontas7 on 2008-08-21
Hi, I'm about to download and install Ubuntu v.8.04 and i have one or two questions depending on how u see it^^

The question(s) are:
Do u have to download different drivers to your main board, graphic card and sound card?
That's the only thing stopping me from downloading Ubuntu at the moment. I dont want to sit there without my graphic card and external hard drive and so on.

Thankful for fast answers ^^ :D

---

### Post by Herman on 2008-08-21
:) Hello jontas7,
Ubuntu will work very well with just about any hardware. There are only a few things that might be hard to get working, maybe if you have very special or extremely new hardware, but it's amazing how well Ubuntu just works all by itself in almost all computers. 
The only way to find out for sure is to try it. It's free so the only thing you might lose is a little of your time.  

Regards, Herman :)

EDIT: To answer your question, no, you don't have to go downloading drivers. In almost all cases, you just install Ubuntu and it will work without the user needing to do any extra work.

---

### Post by kaboodle_fish on 2008-08-21
When you download Ubuntu and burn it to a CD you will have what is known as a LiveCD and that will allow you to check to make sure that Ubuntu works with your hardware without making any changes to your existing set-up

Then you can just install from there once you are happy all is in order.

edit: No you do not have to download different drivers. :)

---

### Post by tuxxy on 2008-08-21
YOu need drivers for your video card yes, this is simple as enabling the driver that Ubuntu provides for you on install.

---

### Post by jontas7 on 2008-08-21
TvM for the answer:D
Very fast and helpful!

Tuxxy u mean that Ubuntu will give me the video driver automatically?

Thanks again :D

---

### Post by tuxxy on 2008-08-21
Yes it should do depending on your card :)

The driver should be supplied to you at system > admin > hardware drivers just tick the box to enable it, if that faails you could install it via Envy, search for envy-gtk in synaptic

---

### Post by lswest on 2008-08-21
> **jontas7 said:**
> TvM for the answer:D
Very fast and helpful!

Tuxxy u mean that Ubuntu will give me the video driver automatically?

Thanks again :D

Assuming you have a (not TOO old) Nvidia or ATI card, then Ubuntu should give you an option to install the drivers needed with minimal input.  It does require a network connection, if it's a wired connection though, there should be no problems.  Wireless might be tricky if it's a laptop, but still usually manageable.  Hope that answered your question sufficiently.

Good luck and welcome to the Ubuntu Forums,
Lswest

---

### Post by jontas7 on 2008-08-21
yes that helped me :D
thanks for all the help, but if u don't mind i have to ask about wireless internet connection.. u can connect to it almost the same way as on windows ?
I'm not some rookie with computers but i would only want to know if there would be any problems configuring my wireless connection ?^^

---

### Post by lswest on 2008-08-21
> **jontas7 said:**
> yes that helped me :D
thanks for all the help, but if u don't mind i have to ask about wireless internet connection.. u can connect to it almost the same way as on windows ?
I'm not some rookie with computers but i would only want to know if there would be any problems configuring my wireless connection ?^^

It depends entirely on your wireless card, chances are you'll have to install windows' inf files for the card (usually from the driver download from the corresponding manufacturer's site) and then install it with a program called ndiswrapper.

Easiest way to do it is to have a wired connection for a bit to install ndiswrapper, but you can also copy ndiswrapper-common and ndiswrapper-utils-1.9 deb files to a USB and install them manually.

Post back what wireless card it is (Intel stuff is generally supported out of the box).  You'll probably know how to check it in Windows, so I'll just go over linux.  To find out what card you have in linux, run the commands ```
lspci
lshw -C network
``` in the terminal (you'll find it under applications-->accessories-->terminal).

Install Ubuntu (or test it on the liveCD, it's generally a good idea to test stuff with it first, to see what will need to be tweaked) first, and if you have wireless issues, you can record the card model, and post back here in a new thread, we should be able to help you better than (lots of ways to do it for different cards, and we don't even know if you'll need it).  Oh, and Ubuntu has an app called nm-applet, which lets you choose wireless networks from a list, and give in the security information, so no big difference to XP's wireless zero config utility.

---

### Post by jontas7 on 2008-08-21
The card I'm using is:
D-Link AirPlus G G510 V.5.10..
But i will try now to install Ubuntu and see how it works and I'll try to fix it ^^

Thx for all the help !

---

