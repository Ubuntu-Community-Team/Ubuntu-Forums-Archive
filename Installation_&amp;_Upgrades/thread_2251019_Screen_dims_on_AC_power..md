---
title: "Screen dims on AC power."
date: 2014-11-01
forum: Installation &amp; Upgrades
---

### Post by jason146 on 2014-11-01
I am new to Linux systems and just installed Ubuntu 14.04 LTS on my Dell Inspiron N5110. 

My screen dims, does not go black, just dims, when I plug in the AC power adapter. I have adjusted the normal settings. I have adjusted the settings in dconf-editor and followed the sintructions here: [http://www.maketecheasier.com/configure-screen-brightness-in-ubuntu/](http://www.maketecheasier.com/configure-screen-brightness-in-ubuntu/) 

I never got the brightness indicator icon on the tray. 

 I have installed caffeine. 

I have tried searching the forums and what I found either did not quite fit my problem, or the suggested fixes were not clear enough for a noob like me. 

Thanks in advance for any help you may offer.

---

### Post by jason146 on 2014-11-07
I got the brightness indicator/adjuster installed on the tray. However, I still have the same dimming issue.

---

### Post by buzzingrobot on 2014-11-08
Have you tried the xbacklight solution mentioned at the end of that MakeTechEasier piece? It's usually used to decrease brightness, but can be set at "100". I've used it on a display that goes very dim when the login screen appears.

---

### Post by jason146 on 2014-11-08
Yes, I did that and set it to 100.

---

### Post by claracc on 2014-11-09
I think, you can find insteresting to solve your problem, the following thread: [http://ubuntuforums.org/showthread.php?t=2199695](http://ubuntuforums.org/showthread.php?t=2199695)

Read all the comments since there are different approaches to the brightness problem.

---

### Post by jason146 on 2014-11-09
> **buzzingrobot said:**
> Have you tried the xbacklight solution mentioned at the end of that MakeTechEasier piece? It's usually used to decrease brightness, but can be set at "100". I've used it on a display that goes very dim when the login screen appears.


I went back and doube checked the startup app info. There was one add-on that was not complete. I believe it was my first attempt to do the backlight solution. I deleted it so that I only had the one completed backlight add-on. 

It looks like that solved the problem. However, I would like to wait another day to verify the fix before I mark this thread as solved.


Thanks for the help everybody.

---

### Post by jason146 on 2014-11-09
I have been on the laptop for about an hour now and it looks to be solved.

Thanks again folks.

---

### Post by nholloway2007 on 2015-03-06
I'm having the same problem on Ubuntu Mate 14.10; I checked dconf-editor, and I don't have a power setting under org>gnome>settings-daemon>plugins. Any help?

---

