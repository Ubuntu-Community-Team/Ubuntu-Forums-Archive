---
title: "[SOLVED] using ENVY to install nVidia 169.07 drivers gets me a HAL initialization err"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by Crinos512 on 2007-12-29
First, some appropriate quotes... (yes... my name is Dave)

> **[Dave Bowman]("http://www.imdb.com/name/nm0001158/")**: Open the pod bay doors, HAL.  
 **[HAL]("http://www.imdb.com/name/nm0706937/")**: I'm sorry Dave, I'm afraid I can't do that.  
 **[Dave Bowman]("http://www.imdb.com/name/nm0001158/")**: What's the problem?  
 **[HAL]("http://www.imdb.com/name/nm0706937/")**: I think you know what the problem is just as well as I do.  
 **[Dave Bowman]("http://www.imdb.com/name/nm0001158/")**: What are you talking about, HAL?  
 **[HAL]("http://www.imdb.com/name/nm0706937/")**: This mission is too important for me to allow you to jeopardize it.
[B]
[HAL]("http://www.imdb.com/name/nm0706937/")[/B]: Just what do you think you're doing, Dave? 

**[HAL]("http://www.imdb.com/name/nm0706937/")**: Dave, this conversation can serve no purpose anymore. Goodbye. 

**[HAL]("http://www.imdb.com/name/nm0706937/")**: I know I've made some very poor decisions recently, but I can give you my complete assurance that my work will be back to normal. I've still got the greatest enthusiasm and confidence in the mission. And I want to help you. 

OK, Enough fun... the details of the matter are as follows:
after using ENVY to update my nVidia drivers to the latest version from the nVidia website (169.07) I get a popup on reboot which reads "Internal error: Failed to Initialize HAL". Synaptic also informs me that the nvidia-glx-new package is broken and needs removed. However everything else seems to be working just fine... compiz, Wolfenstein, UFO:AI, my OpenGL screensaver... all run great!

step 2: using ENVY to remove said drivers fixes the HAL error, which is great if I wanted to run at 800x600, but as expected all programs that like graphics hardware acceleration are not happy.

can someone point me in the right direction to making HAL behave?

---

### Post by Crinos512 on 2007-12-29
nobody?

I know I was joking at first but this is a serious problem. Please, someone help me track down a fix. where should I start?

I attempted running **sudo /etc/initd/hald --daemon=no --verbose=yes** to find out for sure where the break is, but I guess that is not where hald lives.

I used Synaptic to force a reinstall of HAL and DBUS... still getting the error.

:confused::confused:

---

### Post by Crinos512 on 2007-12-30
OK, just realized that the HAL issue is separate from the nVidia drivers.
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931]("https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931")

...but the graphics look great! thanks ENVY!

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[COLOR="Red"]**UPDATE**:[/COLOR] Seems that reverting CONCURRENCY in /etc/init.d/rc back to none from shell solved this for me.

I guess I was loading so fast that GDM was running before HAL and DBUS... oops.
 
(kinda crappy that I can't speed up my boot as much as possible though.)

---

