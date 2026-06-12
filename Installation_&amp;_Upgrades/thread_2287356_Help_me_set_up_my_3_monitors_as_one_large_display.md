---
title: "Help me set up my 3 monitors as one large display"
date: 2015-07-18
forum: Installation &amp; Upgrades
---

### Post by PsychedelicWonders on 2015-07-18
So I have three 24" dell monitors hooked up via two dual Asus Nvidia 9800GT video cards.  

On windows I am able to have them all work together as one large desktop, being able to drag any window or program wherever I want.  I am NOT trying to SLI them into a single monitor.  Right now only 2 actually seem to be active under Ubuntu and I can't seem to get to the 2nd monitor and they both show the task bar on the side.   They aren't mirrored because whatever program I have open does not display on the 2nd monitor.

What do I need to do? 

I'm also getting the following error message upon bootup & getting to the initial Ubuntu login screen & also once I login it pops up again:

Could Not Switch the Monitor Configuration
Could not set the the configuration for CRTC 64

What does that mean and will this error message go away once I get all 3 of my monitors setup correctly?

---

### Post by tgalati4 on 2015-07-18
Your limitation may be the default "superdesktop" resolution of 8096 pixels.  The xorg graphics server paints the display on a superdesktop and your monitors are overlayed on an 8K by 8K grid.  Page through the log file and see what turns up.

Open a terminal:

```
more /var/log/Xorg.0.log
```

Spacebar to page forward, "q" to quit.

Just post the errors or things that look strange.  Don't post the entire file.

---

### Post by PsychedelicWonders on 2015-07-18
I have no idea what to look for and that's a lot of code to read through... is there a way to search for something inside of the terminal?

---

