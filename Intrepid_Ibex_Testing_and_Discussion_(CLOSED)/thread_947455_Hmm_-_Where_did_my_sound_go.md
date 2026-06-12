---
title: "Hmm - Where did my sound go?"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by zoomy942 on 2008-10-14
So I was using my tablet fine, well, since i started using linux 7 weeks ago.  I have been using intrepid since the alpha 4 and things have been fine.

then for no reason, my sound stopped working.  no explanation for it as there were no updates done, and nothing i had changed.  

I still shows up in lspci -v, and alsamixer -Dhw didnt work either. 

There are no errors when i go to test it, it pops up the testing window but i  dont hear anything.

---

### Post by Slug71 on 2008-10-14
Though you have not done any updates have you been keeping up with them? If not it might be a good idea to do some updates or even do a fresh install with the Beta or wait a week for the RC cause there have been a ton of updates since Alpha 4 and a few regarding PulseAudio.

---

### Post by zoomy942 on 2008-10-14
> **Slug71 said:**
> Though you have not done any updates have you been keeping up with them? If not it might be a good idea to do some updates or even do a fresh install with the Beta or wait a week for the RC cause there have been a ton of updates since Alpha 4 and a few regarding PulseAudio.


yeah, i have been following the updates.  i wonder if my audio was just shakey and now it's plain gone

---

### Post by soapytheclown on 2008-10-14
well on mine the other week i was just getting cracking sounds out of my speaker everytime some noise should have been played, i spent days looking for a solution but found none did a fresh install from a daily image and it was back but as of today my sound is gone again back to the crackles (N) 
again it also shows up fine in lspci

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Device 0229
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---

### Post by zoomy942 on 2008-10-14
> **soapytheclown said:**
> well on mine the other week i was just getting cracking sounds out of my speaker everytime some noise should have been played, i spent days looking for a solution but found none did a fresh install from a daily image and it was back but as of today my sound is gone again back to the crackles (N) 
again it also shows up fine in lspci

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Device 0229
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel



thats what happened to mine.  started crackling and then went to nothing

---

### Post by Suzan on 2008-10-14
Killing the pulsaudio process brings back sound.

But that is definately a bug big.. uhm.. big bug.... ;-)

---

### Post by zoomy942 on 2008-10-14
im glad its a known bug.  any bugs i have come across have been fixed really quickly.  I dont mind waiting.

EDIT : killing that process didnt help :(

---

### Post by soapytheclown on 2008-10-14
killing PA only ever worked once for me and it was really random too, im thinking about just re installing off a fresh cd tonight :(

---

### Post by Suzan on 2008-10-14
Yes, we are facing the joy of a beta version. 

Of course killing PA works only for your current session. After a restart, you have to do it again. At least for me it works to get sound back in this session. Setting audio options to "identify automatically" (or what it is in an english Ubuntu) btw.

Well, I just hope it will be OK again with some of the next Updates.

---

### Post by nanog on 2008-10-14
Look for psyke's pulseaudio fix thread. You may also want to play around with your mixer -- sometimes they are messed up in an upgrade. (Right click on speaker and open volume control.)

---

### Post by Delever on 2008-10-14
Cracking sounds fixed by:

installing alsa mixer:

sudo apt-get install alsamixergui

running it:

alsamixer -Dhw

then selecting (with left-right) PCM channel, and pressing UP to increase volume.

I could also increase volume of other channels.

Please, this needs fixing...

---

### Post by zekopeko on 2008-10-14
i don't have ANY sound. and i did a fresh install. i tried padevchooser applet but it's say that the connection to PA server was denied.

---

### Post by zoomy942 on 2008-10-14
after my fresh install today - sound worked again...  but i am nervous she will die again.

---

