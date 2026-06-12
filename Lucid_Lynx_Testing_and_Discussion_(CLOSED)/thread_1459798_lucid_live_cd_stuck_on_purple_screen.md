---
title: "lucid live cd stuck on purple screen"
date: 2010-04-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by inanutshellus on 2010-04-21
I just downloaded the beta 2 ISO for Lucid and tried to install it. Every time I do it gets stuck on the initial loading screen (the one that says ubuntu in white, with a purple background and five dots beneath). 

For about 5 minutes the five dots change color then eventually I hear the CD stop spinning and nothing happens. I couldn't find a keyboard combination to switch me out of the graphical UI to see what might be going on... 

Any suggestions? Is there a way to boot the cd w/o the graphical interface to see what's going on?

I checked the md5sum of the ISO and it was legit. I could end up chalking it up to a bad burn, though the CD loads correctly after I boot normally.

---

### Post by cariboo on 2010-04-21
Have you tried starting using nomodeset? Press the any key at the initial screen, then press F6 and select nomodeset from the menu, then continue on to the desktop.

---

### Post by JHCKX on 2010-04-22
I had similar problems with beta 2 (and beta 1), see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560248](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560248)

In my case it seemed to be related to my video card, an ATI XPRESS Radeon 200M (in a Packard Bell MZ35 laptop). Anyway, what worked for me was to download the latest beta at [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/). The version of April 16 worked fine on this machine.

> **inanutshellus said:**
> I just downloaded the beta 2 ISO for Lucid and tried to install it. Every time I do it gets stuck on the initial loading screen (the one that says ubuntu in white, with a purple background and five dots beneath). 

For about 5 minutes the five dots change color then eventually I hear the CD stop spinning and nothing happens. I couldn't find a keyboard combination to switch me out of the graphical UI to see what might be going on... 

Any suggestions? Is there a way to boot the cd w/o the graphical interface to see what's going on?

I checked the md5sum of the ISO and it was legit. I could end up chalking it up to a bad burn, though the CD loads correctly after I boot normally.

---

### Post by inanutshellus on 2010-04-23
Thanks for the suggestions guys. I used cariboo's suggestion to watch the boot going, and John's suggestion to grab the latest nightly. These two combined (to form Voltron) and helped solve the issue. 

Thank you!

---

### Post by The Cog on 2010-04-23
Another thing to try is simply to switch to tty and back - Ctrl-Alt-F1 then Ctrl-Alt-F7. My laptop seems to put the login dialog off-screen sometimes (on an imaginary second monitor, I think) and this gets it back on screen.

---

