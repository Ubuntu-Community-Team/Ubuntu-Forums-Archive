---
title: "HDMI question"
date: 2012-04-05
forum: Installation &amp; Upgrades
---

### Post by Zettaichi on 2012-04-05
So I have my monitor connected now with my HDMI and it seems like there is something w/ ubuntu that doesnt fully recognize the monitor. I can hear the installation sounds and all but all I see is the shell with nothing.

Any Idea how to fix that?

---

### Post by Lemuriano on 2012-04-05
What version are you using?

---

### Post by Zettaichi on 2012-04-05
Right now i was trying to install 12.04 beta havent try 11.10 yet

---

### Post by Lemuriano on 2012-04-05
For me the HDMI on 11.10 produce video but no sound and on 12.04 everything work like a charm. Did you install the proprietary drivers and sudo apt-get update && sudo apt-get upgrade on 12.04?

---

### Post by Zettaichi on 2012-04-05
I dont even get to that I was ttrying to install ubuntu from the ground as I couldnt use it when I install my new video card.

right now im on win7

---

### Post by grahammechanical on 2012-04-05
Is this when you are running the live CD? Do you get to the screen when you have the option to TRY or INSTALL?

You should look through this thread

[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

You might need to use the nomodeset option to get the live session to run. The problem is not between Ubuntu and the monitor being connected by HDMI but most probably between Ubuntu and the video card needing a proprietary driver. And this you cannot get until Ubuntu is installed.

The X-Server gets the configuration of the monitor through the video card.  And if the X-server has difficulty talking to the video card it cannot go further.

[http://en.wikipedia.org/wiki/Extended_display_identification_data](http://en.wikipedia.org/wiki/Extended_display_identification_data)

Are you sure the HDMI cable is fully compatible? There are different types.

[http://en.wikipedia.org/wiki/HDMI](http://en.wikipedia.org/wiki/HDMI)

Regards.

---

