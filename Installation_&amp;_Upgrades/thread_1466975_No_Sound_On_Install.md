---
title: "No Sound On Install"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by yarnoiser on 2010-04-30
Just upgraded from Ubuntu 9.10 to 10.04. After upgrading, the sound had been lost, there were no sounds of any kind. After that, I did a fresh install, still no sound. I'm not sure what sound card I have, or how to find out. There's also a lingering issue from 9.10 that carried over: in some, but not all games, there is constant mouse and keyboard directional input. I don't touch anything and the player will move. Does anyone know how to fix either problem?

---

### Post by pauljwells on 2010-04-30
Have you tried alsa-mixer? On my Audigy sound card I have to run alsa-mixer, tab along to 'Audigy Analog/Digital Output Jack' and press M (or space, not sure) to un-mute it. Have something playing so that you can hear immediately if you pressed the right thing!

---

### Post by avrono on 2010-04-30
I am having the same problem, in upgrading from 9.04 to 10.04, I no longer have sound. I am sure something is muted. It turns out that it was the ASLA mixer, any ideas how to get the volume control back onto the toolbar ?

---

### Post by eigenadam on 2010-04-30
Run gnome-volume-control-applet from a terminal and that will get it back.

Supposedly volume is on the indicator applet now, but it is missing from mine.

I had to run alsaconf to get my sound to work, but it's not working well. No sound in firefox, and the mic does not work.

---

### Post by doktorOblivion on 2010-04-30
I had to install pavucontrol (pulse audio) volume control, before it would work.

---

### Post by yarnoiser on 2010-04-30
Okay, don't try OSS. That got sound working so that if you go into a room where you can hear a pin drop and set the volume to maximum you can hear the audio very faintly. I'm switching back to ALSA.

---

### Post by yarnoiser on 2010-05-01
Okay, I've solved my audio problem, so anyone having similar problems can follow these directions: first, I'm using an intel HDA sound card and the above posted methods did not work. First, switch to OSS, despite what I posted above, there is a way to boost volume. Use the instructions at this url to install OSS.

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Next, there will be a mention at the above link to a ppa for gnome volume control. This will enable you to adjust volume in OSS without using the terminal. The ppa is at the following url.

[https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

Follow the instructions for adding this location to your software sources. Then go to your menu bar: System, Administration, Synaptic Package Manager. Press the "Mark All Upgrades" button and hit apply. This will remove "Sound" from your preferences menu, but it doesn't work with OSS anyway. Then, right click on one of your panels and hit "add to panel". Choose "volume control" from the menu, this volume control will not appear in any menus, that threw me off the first time I tried this. Select preferences in volume control, try the switches and options one by one, one of them should do something if your getting even minimal audio, just keep looking until you find it.

OSS for the WIN!!!

---

