---
title: "No sound on virgin install 9.10, ASUS L8400 laptop"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by roderick.young on 2009-11-13
I am completely new to Ubuntu, and have a tip for those accustomed to Windows. If you're a newbie like me, skip to the bottom for the solution. If you're seasoned in Linux, skip this thread entirely, nothing to see here.
 
After installing this OS (and completely erasing and using the whole disk), I couldn't get the sound to work. Playing around with the preferences, it seemed that there was a sound driver installed. At least one other person on the web said that they got their Asus L8400 to work without incident. I then proceeded to search the web, and found out about the lspci command, ESS1988 chip, snd-maestro3 driver, alsamixer, special firmware required at one point for this chip. I went to the volume control and turned the slider all the way up, as well as bringing everything up in the alsamixer. I reinstalled the driver, force-reloaded the sound module. Nothing helped.
 
The problem was my Windows mindset, that sound will be there, and must be deliberately turned off if desired. A few things are different in Ubuntu.
 
1. The default on a fresh install is for sound to be *disabled*.
 
2. The mixer, at least alsamixer, does not have check boxes to mute various outputs. Since I saw the levels as being non-zero, I assumed that sound would come out.
 
3. The volume control on the top right of the screen does not change appearance to have a red "prohibit" circle over it when sound is muted. Maybe it went gray or something, but I was not used to this paradigm.
 
4. Left-click on the volume control brings up the volume slider, but no mute button is shown. As a newbie, I assumed that there was therefore no mute function on the volume control. I learned later (much later) that one must right-click on the volume control to see the "mute" selection.
 
Solution: right-click on volume control at upper right, un-check the Mute option.

---

### Post by kaizilla on 2010-01-14
Thank you for sharing your experience.;)
how's the speed the 9.10 running on L8400. I'm holding one of this PIII as well:D

---

### Post by kronictokr on 2010-02-14
try this, has various fixes included, works like a charm

[http://swiss.ubuntuforums.org/showthread.php?t=1395089](http://swiss.ubuntuforums.org/showthread.php?t=1395089)

---

