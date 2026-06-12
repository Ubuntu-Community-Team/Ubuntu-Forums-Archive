---
title: "Newly installed Ubuntu Studio - X server issues"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by Translated on 2007-06-14
It won't load up the graphical X server...  I'm new to linux, one of the errors reported was that Timidity hadn't started up... etc...

Not sure where to go from here.

---

### Post by ggaaron on 2007-06-14
Timidity is an application to play midi, nothing to do with xserver.

Login in terminal and type startx - it'll give you some errors, but probably xorg is wrongly configured... Run sudo dpkg-reconfigure xserver-xorg, and configure it.

---

### Post by Translated on 2007-06-15
Yep, that turned out to be the problem... I had the wrong video card drivers selected....

I'm having issues with the Audio programs, I keep getting a message saying that JACK hasn't started up or isn't running?  

Could it have something to do with Timidity not starting up properly ?

---

### Post by Patrick K on 2007-06-15
In the Sound and Video menu click on qjackctl. This will start the jack server and provide a GUI for configuring and controlling jackd.

---

### Post by Translated on 2007-06-16
Sweet!!!  Thanks alot.

---

