---
title: "upgrade frm hardy to interpid via cd??"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by tgpraveen on 2008-10-25
SO i have a nicely running ubuntu 8.04 hardy. i have set it up as i want.
but the thing is i have a dual boot system and my net works only in  windows bcoz of a wireless modem with support only in windows.
so in ubuntu 8.04 i dont have net.

so if i download ubuntu 8.10 via windows and burn it to a cd. and boot from that cd will i be able to upgrade from that cd.

the thing is that my current hardy system is configured well by me and i dont want to loose it.

THE MAIN THING that i dont want to loose are the codecs and restricted drivers that i have installed in hardy ( i installed that earlier when  i had a wired net connection whcih worked in ubuntu).
so can i do this i dont want to loose my codecs as i wont be able to install them again. and without them my ubuntu will be very useless.

pls help.
thx in advance.

---

### Post by Pumalite on 2008-10-25
Four caveats:
1.-You have to have your system fully updated before attemptying any upgrade
2.-You nee the Alternate CD to upgrade in that fashion
3.-You need to remove all third parties from your /etc/apt/sources.list
4.-You need to delete the Medibuntu folder if you have one

---

### Post by tgpraveen on 2008-10-25
oh man this seems to be a bummer
1. as i dont have net on ubuntu its not updated for a while
2.alternate cd usage aint much of a problem if it has the same gui interface of the normal cd(hey i am somewht of a noob). secondly r u sure i cant do it using the main cd.
3. removing 3rd parties can be done so no probs here.
4. pls give more details what u mean by medibuntu folder?

---

### Post by tgpraveen on 2008-10-26
someone pls reply

---

### Post by sdowney717 on 2008-10-26
use the DVD iso.
just disable the third party software sources. 
OR
perhaps be prepared to do a new install, back up all your codecs, players, etc... and user space. Your home folder can be used as a new user in the new install
 
so far ibex is good so it is worth upgrading.

---

### Post by aaronb on 2008-10-26
If there is no other way then I would temporally move the PC so that you could use the wired connection for updating.

Also it may be worth checking to see of there is any workarounds to get Wifi working in ubuntu as I've seen some threads on people using Windows drivers via a tool called ndiswrapper.

---

### Post by tgpraveen on 2008-10-26
> **sdowney717 said:**
> use the DVD iso.
just disable the third party software sources. 
OR
perhaps be prepared to do a new install, back up all your codecs, players, etc... and user space. Your home folder can be used as a new user in the new install
 
so far ibex is good so it is worth upgrading.


What do u mean by the dvd iso. i thought there was only the standard cd iso. link pls.

How do i back up my codecs,etc. if i just copy paste my home folder will it do? what stuff could i loose? this option seems good. pls elaborate.

---

### Post by sdowney717 on 2008-10-26
The dvd iso has all the packages or most of the best ones.
You home folder can be simply copied and then restored.
Do a search on backing up your home folder for the details. 
I believe you can simply do something along this way:

install the new distribution using the dvd iso
recreate your old user login.
copy your home folder back over.

a quick google for example like this for dvd iso 

[http://cdimage.ubuntu.com/ubuntustudio/daily/current/](http://cdimage.ubuntu.com/ubuntustudio/daily/current/)

I dont think they have released ibex yet but you will absolutely find it when they do.
[http://nginyang.uvt.nl/](http://nginyang.uvt.nl/)
[http://ubuntu-8-1.blogspot.com/2008/08/free-ubuntu-804-cd-or-dvd-iso-torrent.html](http://ubuntu-8-1.blogspot.com/2008/08/free-ubuntu-804-cd-or-dvd-iso-torrent.html)

which codecs are you thinking of preserving?
name the programs

---

