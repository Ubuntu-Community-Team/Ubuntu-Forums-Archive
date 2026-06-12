---
title: "Ubuntu on a Dell Inspiron 9300"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by InDreamz on 2005-10-14
OKay here is my problem. I am attempting to install ubuntu on my Dell Inspiron 9300. The intial screen comes up fine, the one where it says hit enter to install or F1 for options. I hit enter and it runs for a moment then when it comes to where I guess a GUI should be the screen just turns blue with a white haze that slowly spreads outward. In new to Linux and really need some help

---

### Post by audax321 on 2005-10-14
EDIT: Never mind, I misunderstood you so just disregard what I wrote below. Although that could be useful if you can't get into the GUI after you actually install it. So, basically you can't even get into the installer? That's odd. I have no idea what to do then. What you could do is download the Hoary CD (which I've used before) and as soon as you get into Linux edit /etc/apt/sources.list and change all references of hoary to breezy. Then you can just open up a terminal and do sudo apt-get update followed by sudo apt-get dist-upgrade and that will upgrade you to breezy without having to use the installer.

------ My previous post, probably won't work if the installer can't start.
I used to have an Inspiron 9300 that worked with Hoary so something is probably just wrong in your xorg.conf.

Can you do CNTRL+ALT+F6 and access a prompt?

If you can, log-in with your username/password and then type:

nano /etc/X11/xorg.conf

Post the part that says Section "Device" (it has some info about your video card) and Section "Monitor (has info about the refresh on your monitor).

I'll see if I can find my old config, should be backed up somewhere. Also what is the highest resolution on your screen?  I had the 1920x1200 one.

---

### Post by InDreamz on 2005-10-14
Forgive me for not being clear before. I am new to the forum world as I am the Linux world. This white screen of Death appears as I am trying to install ubuntu. I boot from the CD I get the ubuntu logo and the options to hit F1 for advanced options, enter to install linux. I hit enter and it begins uncompressing. As soon as the uncompressing is finished and it goes to load what I assume is to be a GUI I get this hazey blue and white screen, like something you would  see out of a bad sci fi movie. No matter what key combinations I hit nothing happens.

---

### Post by audax321 on 2005-10-14
Try this. I found this website about Breezy on that laptop:

[http://rtr.ca/dell_i9300/breezy.html](http://rtr.ca/dell_i9300/breezy.html)

I think you have to enter "linux vga=771" at the prompt to get it to work.

---

### Post by InDreamz on 2005-10-20
Thank you for your help that fixed my problem. 












(\ /)
(O.o)
(> <)

This is Bunny. Copy Bunny into your signature to help him on his way to world domination.

---

