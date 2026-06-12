---
title: "Need advice on installation options."
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by Ifaistos on 2012-04-29
Hello everyone :-)

One of my friends was convinced to convert to Ubuntu :-)
So of course I offered to do that for him.  It's always nice to take laptops and switch them from VISTA to Ubuntu ... hehe...

Anyway.. I am facing problems though :(

His laptop is the Fujitsu-Siemens Amilo La1703.
It has a 64bit processor, with the following gfx card...

===================================
VIA S3G UniChrome Pro: The S3 UniChrome (Pro) is a DirectX 7 (without T&L) onboard graphic solution (shared memory) from VIA for laptops. Mainly, it is intended for office activities and hardly suited for 3D games.
=====================================

This comment is taken from here :
[http://www.notebookcheck.net/Fujitsu-Siemens-Amilo-La1703.3132.0.html](http://www.notebookcheck.net/Fujitsu-Siemens-Amilo-La1703.3132.0.html)

The installation was flawless.
It was a clean install, which I formatted VISTA (yeah!!) into 3 partitions..

root - 22GB
swap - 3GB
home - all the rest (around 130 GB).

I used the 64bit version of ubuntu.
I believe the problems that I am facing are from the gfx card.
It doesn't run Unity 3d.
I installed ccsm, in the beginning from the software center, but it didn't have all the options.  So I did this in the terminal :

>> sudo apt-get install compiz compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-plugins <<

Which I found here :
[https://help.ubuntu.com/community/CompositeManager#Install_CompizConfig_Settings_Manager](https://help.ubuntu.com/community/CompositeManager#Install_CompizConfig_Settings_Manager)

I followed the steps described in the page above, but I had the following problems:

-- First of all Ubuntu didn't detect any proprietary drivers for the gfx card.  

-- Never asked me anything about OpenGL.

-- In the options in CCSM, there is no option for : Desktop Size.  It just doesn't exist.

-- When I right click on the desktop and choose to change background, on other computers I can see the option to change the size of the icons in the launcher.  In this one... no.

-- Also there should be an option for "visual effects" and then extra... it doesn't exist.

-- When I type "compiz --replace" to force compiz to start, the gfx card goes crazy.  The display goes crazy, doing weird stuff... I can see the icons on the launcher become smaller.. which is the setting I've set on ccsm, and unity plugin.

-- However after a while the system crashes and it becomes inoperable.  I managed to see a report on the terminal, saying : "This shouldn't have happened.  You should probably file a bug report"... but other than that, I could copy the contents of the terminal, and post it here because as I told you the laptop was inoperable.... NOT STUCK... everything was active, but I couldn't click the mouse, or change into other applications...  The GUI was totally screwed up.

Anyway.. could I have some advice of what I should do?
I told my friend that with Ubuntu his laptop would run much faster and smoother.

* Should I install a 32bit version?
* Should I go for the 2D version and tell him that his card doesn't support the 3D environment?

Any other suggestions?
Thank you all for your support.

---

### Post by kc1di on 2012-04-29
There is a ubuntu page about that video card here:

[https://help.ubuntu.com/community/OpenChrome]("https://help.ubuntu.com/community/OpenChrome")

But it's pretty old. May be of some help though.  
From what I gather it's difficult to do 3d with and you may be stuck with 2d .
good luck,
D ;)

---

### Post by Ifaistos on 2012-04-29
Thank you for the info :)

It may be the case that this gfx card, will never do 3D properly :(

Anyway... 
Anyone with some more recent info/developments/ideas?

---

### Post by whiskers751 on 2012-04-29
Can you press ctrl+alt+f1 at the messed GUI or press ctrl+alt+bksp?

---

### Post by Ifaistos on 2012-04-30
Nope it doesn't work.
I've tried that...

Thanks.

---

