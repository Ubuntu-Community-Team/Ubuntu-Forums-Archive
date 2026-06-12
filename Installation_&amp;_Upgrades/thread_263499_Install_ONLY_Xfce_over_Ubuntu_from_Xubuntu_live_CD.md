---
title: "Install ONLY Xfce over Ubuntu from Xubuntu live CD?"
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by vynsane on 2006-09-23
just like the title says, can i "install ONLY Xfce over Ubuntu from Xubuntu live CD?"

i'm in the middle of converting my second computer, a dell inspirion 7500 laptop at 600mhz, from windows to (x)ubuntu. i already did a dual boot of the old win98 install with xubuntu (which ran IMMENSELY faster than the windows install, btw) but i wanted to get rid of windows when i knew that xubuntu would work on the system. 

however, i wanted more programs than come with xubuntu (namely openoffice...) and i don't have ANY network capabilities - all i have is a 56k modem (i don't even have a phoneline at home!) and a linksys wireless pc/mcia card that xubuntu didn't recognize. i know i need to install the win driver with the ndiswrapper, and i'll tackle that when i have the time, but for now i just want the faster and (imo) nicer looking xfce installed over ubuntu, so i get the gnome apps.

i've already installed all three desktop environments on another system, and know how to do it with network access, but how can i install Xfce onto my ubnutu install using the xubuntu live cd (if at all)?

---

### Post by reacocard on 2006-09-23
You can't with the livecd, but the alternate cd should work fine for this.

---

### Post by K.Mandla on 2006-09-23
It's been a long time since I did this, but reacocard is right. If you put a standard Ubuntu alternate/install CD in your drive, then enter *sudo apt-cdrom add* in a terminal, it will add the packages on the CD to your list of installation candidates.

From there, you should be able to *sudo aptitude update* then *sudo aptitude install* anything you like. 

Remember that adding OpenOffice is going to weigh down your system considerably.

---

### Post by vynsane on 2006-09-23
thanks for the point in the right direction, reacocard...

> **K.Mandla said:**
> It's been a long time since I did this, but reacocard is right. If you put a standard Ubuntu alternate/install CD in your drive, then enter *sudo apt-cdrom add* in a terminal, it will add the packages on the CD to your list of installation candidates.

From there, you should be able to *sudo aptitude update* then *sudo aptitude install* anything you like. 

Remember that adding OpenOffice is going to weigh down your system considerably.

cool, thanks for the specifics, K.Mandla. i've already installed ubuntu on the laptop, and brought up OOo... it's not really that slow (lightspeed compared to win98 in both Gnome and Xfce...) so i'm not too concerned. it's 600mhz, but i think it's got something around 384mb of ram.

if i am correct, in this way i should be able to add the cd drive as an installation candidate, i can then 

```
sudo aptitude install xubuntu-desktop
```

from the xubuntu alt cd to write xfce onto my ubuntu install? thanks again, both of you. linux is fun! it's spreading like wildfire among all my computers...

---

### Post by K.Mandla on 2006-09-23
> **vynsane said:**
> if i am correct, in this way i should be able to add the cd drive as an installation candidate, i can then 

```
sudo aptitude install xubuntu-desktop
```

from the xubuntu alt cd to write xfce onto my ubuntu install? thanks again, both of you. linux is fun! it's spreading like wildfire among all my computers...
Yup, that should do it. Good luck. Post if you run into problems.

---

### Post by vynsane on 2006-09-23
worked like a charm. good to know what can be done with the alt cd, too. thanks again!

---

