---
title: "Intel HD2000/HD3000 Graphics Drivers with Maverick 10.10"
date: 2012-01-25
forum: Installation &amp; Upgrades
---

### Post by dazman19 on 2012-01-25
I need to use Maverick for XBMC. I have tried and failed to get it working in 11.10. And i dont really want to use Beta.

Been googling this but it doesnt seem that maverick has support for the sandy bridge GPU.

Unless anyone knows how to get the graphics drivers working properly on maverick, then i guess my best option is to buy a nVidia graphics card.? 
Any help? Anyone had similar problems?

Hope someone has a link or something.

---

### Post by mastablasta on 2012-01-25
try to install x org edgers PPA (these are latest opensoruce drivers for the GPU): [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
 
though support for porcessor is porbably in kernel. i am not sure why you couldn't ge ti running. 
 
if edgers PPA is not working then another option is to upgrade kernel and then drivers.

---

### Post by dazman19 on 2012-01-25
thanks heaps for the suggestion.
I will give this a go tonight. Let you know how I get on.

---

### Post by dazman19 on 2012-01-26
Im trying to install this now. I read through the page, but it doesnt seem to tell you how to do it. I managed to add the PPA. 

whats next? 

I can see the list of published packages. But which ones do i install?? All of them?? And do i need to do anything.. e.g. is there a magic command like 

sudo apt-get install somepackage which will help me to set up the driver?

i tried this, but i really dont know what i am doing sudo apt-get install xserver-xorg-video-intel

---

### Post by mastablasta on 2012-01-26
well after adding the PPA the packages will show up in software center. if you click on the packge it will give you a description of what it is.

---

