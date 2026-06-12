---
title: "Hardy killed my Wireless."
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by rbolio on 2008-04-27
So, here is the deal. I Upgraded from 7.10 to 8.04 and first thing I noticed was that my wireless icon was not turned on (the hardware one.) so i messed around with the computer but still no luck.
After searching the forums I realized that i needed some file called ndisgtk. 

so the problem is that i cant sudo apt-get it. (o yeah forgot to mention my LAN hardware is broken ha).


So if there is a place i can download ndisgtk to a usb so i can later pass it to my laptop (and how do i install it, im still kinda new to ubuntu) 

PS. just in the case it is needed ---> 
i have a dell inspiron 6400 with a Intel PRO/wireless 3945ABGnetwork card 


Thank you!

---

### Post by rbolio on 2008-04-28
===BUMP==


btw> i mixed up and it is a Broadcom BCM 4401-B0 100 Base-TX (rev 02)

---

### Post by MBro on 2008-04-28
you don't need ndisgtk, it helps but isn't required.

Pop in your install cd and open synaptic and make sure the cd is part of your repo selection.  Update your lists.

Then search for ndiswrapper and install that.

Pop in your windows wireless driver cd and copy the windows xp driver to your home folder.

open a terminal and install the driver with the ndiswrapper command (I don't have it installed and haven't used it in a year so I don't know off hand, ndiswrapper -help should tell you)
I know you need to install the driver and the device and the write it to modprobe.

After you do the ndiswrapper stuff run sudo modprobe ndiswrapper.  You may need to -r your old driver.

---

### Post by rbolio on 2008-04-28
okay ill try all of that, but is it okay if the cd is for gutsy and not hardy? (downloaded hady) 

ill try later today (did't bring my laptop)  and ill post results.

once more, thank you.

---

### Post by rbolio on 2008-04-28
Okay things are moving smoothly...kinda heres where i'm stuck.

installed ndiswrapper succesfully but when i tried to do the modprobe thing (really have no idea what that is \ how its done) but things were not working , so, heres what i put later in terminal

rbolio@buntu: ~$ ndiswrapper- l
b44win: invalid driver

rbolio@ubuntu: ~$ ndiswrapper -i b44win
driver b44win is already installed 

... so i tried to remove

rbolio@ubuntu: ~$ ndiswrapper -r b44win
Couldn't delete /etc/ndiswrapper/b44win: inappropriate ioctl for device


HElp

---

