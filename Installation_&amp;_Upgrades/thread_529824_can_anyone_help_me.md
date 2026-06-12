---
title: "can anyone help me?"
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by kdxrider9262 on 2007-08-19
Hello,

Are there any guides for n00bs to set up a low latency server? I have NO idea how to compile my own kernel.

---

### Post by kerry_s on 2007-08-19
If i remember right, you don't have to compile, it should be in the repo. all you have to do is install it than reboot and select it in the grub menu. if you have gui, just open synaptic and search "linux-image". if you don't have gui, type> sudo aptitude <then press> / <and search "linux-image"> n <is to go to the next search hit. press shift ? for the help page.

---

### Post by kdxrider9262 on 2007-08-19
alright...sorry im a bigger n00b than you thought at linux lol........lets say I have a fresh formatted HD and a blank cd.........where do I go from here LMAO

---

### Post by kerry_s on 2007-08-19
> **kdxrider9262 said:**
> alright...sorry im a bigger n00b than you thought at linux lol........lets say I have a fresh formatted HD and a blank cd.........where do I go from here LMAO

LOL, okay, start by getting the server edition->
[http://www.ubuntu.com/products/whatisubuntu/serveredition](http://www.ubuntu.com/products/whatisubuntu/serveredition)

just in case you don't know how to burn a iso->
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

then read up->
[https://help.ubuntu.com/7.04/server/C/](https://help.ubuntu.com/7.04/server/C/)

let me know when you get stuck. :)

reminder, servers are non-gui, that means it does not have a desktop. but a gui can be added.
incase you want a gui->
sudo apt-get install xorg gdm icewm menu mc

---

### Post by kdxrider9262 on 2007-08-20
I have server edition already installed with XFCE 4.......but I thought I had to like start over to get the 1000hz interupt

---

### Post by kerry_s on 2007-08-20
> **kdxrider9262 said:**
> I have server edition already installed with XFCE 4.......but I thought I had to like start over to get the 1000hz interupt

okay, press> alt+f2 <type> gksu synaptic <click on search,type> linux-image <enter, look for the 1 that says lowlatency. i can't tell you exactly what it say's cause i'm on debian and are kernel setup is different. when you find it, right click> mark for installation, then click apply. after it's finished installing you just reboot and select it in the grub startup and your good to go.

---

### Post by kdxrider9262 on 2007-08-20
thank you for you help thus far....I did as you said and I could not find one that said anything about low latency......There were a couple for different processors and some for bigiron servers.....what ever that is.......any other ideas?

---

### Post by Pumalite on 2007-08-20
linux-image-lowlatency  2.6.20.16.28.1

---

### Post by kdxrider9262 on 2007-08-21
i copied what you said to search for and nothing came up :(

---

### Post by Pumalite on 2007-08-21
Check your repos. I you want to I'll send you a copy of mine.

---

### Post by kdxrider9262 on 2007-08-21
I havent changed any of the repos really.....I only added the ones to install nxserver.......if you want to send me yours that would be great......Thanks

---

### Post by Pumalite on 2007-08-21
I sent you a PM.

---

