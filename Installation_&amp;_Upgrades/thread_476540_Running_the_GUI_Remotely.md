---
title: "Running the GUI Remotely"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by doncam on 2007-06-17
I have installed Fiesty on a box that lives in a closet in the furnace room.  while Installing it, I had a monitor, keyboard, and mouse hooked directly to the box and the GUI worked great.  I would now like to access the GUI from my XP box using xming X server.  I can run xclock from the XP box so I know permissions, etc are working in xming.  I used X extensively a few years back but am kinda rusty.  How do I configure my .xinitrc to bring up the GUI remotely when I do a startx?

TIA


dc

---

### Post by Persianelfster on 2007-06-17
Why can't you just use Xlauncher select plink and then ip of your remote machine, then your username and password.  and keep the application xterm. Then form xterm run sudo /etc/init.d/gdm start 
However it might take a long time to start =/

---

### Post by Persianelfster on 2007-06-18
Im sorry what i meant was start an XDMCP session
with the meathod above you can run fluxbox sorry for the mistake =(

---

