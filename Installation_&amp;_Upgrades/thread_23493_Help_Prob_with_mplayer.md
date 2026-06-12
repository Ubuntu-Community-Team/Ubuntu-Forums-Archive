---
title: "Help Prob with mplayer"
date: 2005-04-02
forum: Installation &amp; Upgrades
---

### Post by Nez7165 on 2005-04-02
I have updated my synaptic packege to receve unerfitial deb packeges. I am trying to install mplayer. When i do it tells me i need certain dependencys that can install so i installed them manually. Yet one will not work. I installed libjack0.80.0-0. I then need to install libbio2jack0.
When i click on it this error comes up please help

Depends: libjack0.80.0-0 but it is not going to be installed

---

### Post by feneks on 2005-04-02
Try this in a terminal or console:
```
sudo apt-get -f install
```
and then 
```
sudo dpkg --configure -a
```

Let's see if this helps.

---

### Post by Nez7165 on 2005-04-04
Hay unfortuanatly that did not work. It says the same thing exept it says that it should be installed but something else is going 2 install. it says 0.xx. 3ubuntu3 is going 2 install. Im not infront of my pc right now so unfortuantly i cant tell u the exact error if u need more please post and ill put it up on Tues 5 when im home. Thanks

---

### Post by feneks on 2005-04-04
The full output would be fine. Otherwise I'll have to guess a bit.

---

### Post by Nez7165 on 2005-04-05
I have just done a upgrade and am now getting more problems as well as the one before.

when i mark for installation this is wat i get 

mplayer-586:
  Depends: libartsc0 (>=1.3.2) but 1.2.3-1 is to be installed
  Depends: libasound2 (>1.0.8) but 1.0.5-woody0.1 is to be installed
 Depends: libbio2jack0 but it is not going to be installed
  Depends: libfontconfig1 (>=2.3.0) but 2.2.2-2ubuntu3 is to be installed
  Depends: libggi2 (>=1:2.0.5) but 1:2.0.4-3 is to be installed
  Depends: libglib2.0-0 (>=2.6.0) but 2.4.7-0ubuntu2 is to be installed
  Depends: libjack0.80.0-0 (>=0.99.0) but 0.98.1-3ubuntu3 is to be installed
  Depends: libogg0 (>=1.1.2) but 1.1.0-1 is to be installed
  Depends: libpng12-0 (>=1.2.8rel) but 1.2.5.0-7ubuntu1 is to be installed
  Depends: libsdl1.2debian (>1.2.7+1.2.8) but 1.2.7-7 is to be installed
  Depends: libungif4g (>=4.1.3) but 4.1.0b1-6 is to be installed
  Depends: libvorbis0a (>=1.1.0) but 1.0.1-1 is to be installed

When i go and try to install libbio2jack0 on its own this is wat i get 

libbio2jack0:
  Depends: libjack0.80.0-0 (>=0.99.0) but 0.98.1-3ubuntu3 is to be installed

please help
 Thanks
P.S if i try and install mplayer 686 withch is wat i need it says 585 wont install

---

### Post by Nez7165 on 2005-04-05
Hay ok i have got down 2 these last few ones and i dono how 2 update them the otheres i downloaded the .deb files and did the updates.
mplayer-586: Depends: libbio2jack0 but it is not going to be installed
               Depends: libfontconfig1 (>= 2.3.0) but 2.2.2-2ubuntu3 is to be installed
               Depends: libjack0.80.0-0 (>= 0.99.0) but it is not going to be installed
               Depends: libsdl1.2debian (> 1.2.7+1.2.8) but it is not going to be installed

Thanks

---

### Post by Nez7165 on 2005-04-05
Depends: libfontconfig1 (>= 2.3.0) but 2.2.3-4ubuntu7 is to be installed
               Depends: libsdl1.2debian (> 1.2.7+1.2.8) but it is not going to be installed
now down to this
 
When i upgraded the libfont i think i used a wrong thing cause it got broken so im bk to these 2 and cant find any help

---

### Post by Nez7165 on 2005-04-05
Cheers 4 all your help but i have actually sorted the problem now and mplayer works. I now have a sorta diff prob tho i dono if u can help. Now when i install programes it dose not add them to the aplications drop down menus.

Thanks

---

### Post by feneks on 2005-04-05
First:
You did a very good job! Congratiolations!

But I'm sorry, I'm neither a GNOME-guru nor do I know how automatical addition to menus works.  :(  
If you aren't using .debs from the Ubuntu-servers this might be a reason. The .debs from Debian Linux are often installed to a special menu-folder called "Debian". This is somehow an application-menu in the application-menu. Doesn't  sound good, actually it's a bad makeshift. At least you can find the applications but it's just for Debian I guess. 

Hopefully you'll find out.

---

