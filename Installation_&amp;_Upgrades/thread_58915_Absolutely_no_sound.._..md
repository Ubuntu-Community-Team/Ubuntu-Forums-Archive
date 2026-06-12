---
title: "Absolutely no sound.. ."
date: 2005-08-22
forum: Installation &amp; Upgrades
---

### Post by Eleaf on 2005-08-22
Hello..  I've recently installed ubuntu on my g3 iBook..  My 10 gig hard drive was completely messed up and I ended up having to use my smaller 3 gig hard drive.  It seemed like doing a normal installation was taking up way too much space so I did a 'server' install and then added my window manager.  I tried quite a few and decided to just go back to gnome.  To avoid it taking up so much spaces and installing things I don't need, I just did an apt-get install gnome-core.  This installed quickly and I had a working system!  It runs fine and looks great.  I love it!

But I have now noticed there is no sound!  I've been reading forums about what might be the cause of this for about all day today and some yesterday..  I am yet to find any actual answer..  I've checked things like the alsamixer and put everything up...  I don't think its seeing my sound card at all!  Because when I do any of the /proc/ sound thingies just nothing shows up...  I really don't get this.

I'm going to need sound and I just don't know what to do...  Does anybody know how to set up sound from this point??  Thanks.   ](*,)

(Edit:  I do have sound but only for the terminal "beep" sound that is heard either in a terminal or login shell when you hit delete.  That is the ONLY sound that will ever play.)

---

### Post by lol on 2005-08-22
I have a G3 Powerbook, and to enable sound, I have to load one of the following module : dmasound_pmac (oss) or snd_powermac (alsa)

Just choose if you want alsa or oss and add the corresponding module in /etc/modules to load it at boot time.

---

### Post by Eleaf on 2005-08-22
Alright thanks..  I tried that but its already there anyways..  Thanks though..  Any more ideas? = /

---

### Post by Eleaf on 2005-08-22
I'm doing and apt-get install gnome to install the entire gnome system.  Maybe installing just the core excluded some files needed for sound support.  I'll try it out.. =P

---

### Post by Eleaf on 2005-08-22
That was it!  It turns out that just the core gnome system doesn't have enough for sound support.  Just enough for a usable desktop environment without it..  My space is pretty low now..  I'm going to try and get rid of some of the stuff i don't need now from doing a full gnome install but sound and everything works!!  Great!  This will be good and I'm getting a larger drive soon anyways..  Cool! =-)

---

### Post by twelvegates on 2005-08-22
[QUOTE=Eleaf]
But I have now noticed there is no sound! [/QUOTE]
Is the volume control in the panel working?
What does *l`smod | grep snd`* say?
What does *`ps wax | grep esd`* say?

-Hanspeter

---

