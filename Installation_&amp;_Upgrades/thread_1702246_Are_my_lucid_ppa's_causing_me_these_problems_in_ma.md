---
title: "Are my lucid ppa's causing me these problems in maverick?"
date: 2011-03-07
forum: Installation &amp; Upgrades
---

### Post by maddbaron on 2011-03-07
Problems after upgrading to maverick from lucid:
1 - Can't activate special effects
2- panel tearing/applet's vanishing
3 - youtube/multimedia playback with gray or black boxes where videos should be but with audio

All my ppa's say lucid at the end and i've updated software,  do I need to replace all of the ppa's i currently have so they read maverick at the end then update or are these problems a result of something else?

any help would be appreciated.

---

### Post by gordintoronto on 2011-03-07
I don't think you successfully upgraded to Maverick. Can you describe what you did?

---

### Post by maddbaron on 2011-03-07
> **gordintoronto said:**
> I don't think you successfully upgraded to Maverick. Can you describe what you did?

de-enabled my 3rd party ppa's
changed from LTS to normal
used my ethernet cable instead of wifi
upgraded from 10.04 to 10.10 
the upgrade took a ton of hours then rebooted 
spent two weeks tryin to fix my display
fixed my display now i can't enable special effects and my video online and offline won't play but the sound of them will.

---

### Post by Frogs Hair on 2011-03-07
Your Youtube problem sounds flash related , I switched to FF4 beta and had use flash aid to correct the same problem with one site . The other thing I was wondering is , what proprietary drivers and graphics card are you using ? The proprietary drivers you had on 10.04 would have been removed during the upgrade if you did not remove them yourself.

---

### Post by maddbaron on 2011-03-07
> **Frogs Hair said:**
> Your Youtube problem sounds flash related , I switched to FF4 beta and had use flash aid to correct the same problem with one site . The other thing I was wondering is , what proprietary drivers and graphics card are you using ? The proprietary drivers you had on 10.04 would have been removed during the upgrade if you did not remove them yourself.

I fixed the drivers, i removed then reinstalled them didn't know i had to do that at the time but now they are installed. 

i fixed my video on my pc problem except in vlc player where the video is now black & white and squeezed to the left of the screen...but mplayer and totem work normally again

flash, i removed my flash player and installed the nonfree version which had a maverick in it, the other flash still had lucid but i still get the gray screen.  what is the flash aid?

any idea on how i can enable effects on desktop? when I try it says driver not found but i check and the system says driver installed and working properly. is there a different driver for desktop effects?

---

### Post by tophousetim on 2011-03-07
Take a look at the following. Many have had this problem. [https://bugs.launchpad.net/bugs/653933](https://bugs.launchpad.net/bugs/653933)

---

### Post by Frogs Hair on 2011-03-07
If you installed the recommended driver from additional / hardware and  drivers that is the correct one. I suggest you search  for threads desktop effects because many people have had the same problem. I'm assuming you have Compiz installed.

Flash aid was developed by a Ubuntu forum member , you can read the description at the link. 
[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by maddbaron on 2011-03-07
> **Frogs Hair said:**
> If you installed the recommended driver from additional / hardware and  drivers that is the correct one. I suggest you search  for threads desktop effects because many people have had the same problem. I'm assuming you have Compiz installed.

Flash aid was developed by a Ubuntu forum member , you can read the description at the link. 
[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

yeah i have compiz installed, i have removed and reinstalled it thinking it was wrong but its not i guess... i'll keep looking for a fix...gotta update my ppa's though i was hoping to find a script to do so automatically but none exists lol... 

thanks for the help and the link

---

### Post by maddbaron on 2011-03-07
> **tophousetim said:**
> Take a look at the following. Many have had this problem. [https://bugs.launchpad.net/bugs/653933](https://bugs.launchpad.net/bugs/653933)

i see there is no fix still... this sucks i miss compiz, i can't activate the unity 2d desktop yet either... i hope its fixed soon

---

