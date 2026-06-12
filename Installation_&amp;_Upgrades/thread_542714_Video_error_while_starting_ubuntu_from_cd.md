---
title: "Video error while starting ubuntu from cd"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by Amun11 on 2007-09-04
Hello,

I am a first time user, and have no experience at all with linux or ubuntu. I downloaded the latest version of ubuntu, and burned it. While booting from the cd, it gave an error message. I can't remember the exact words, but it said something like: Problem with X Server (Video interface), and that it was nescesary to configure it correctly. Can somebody help me with this? If more info is needed, just ask...

Thanks!

---

### Post by Pumalite on 2007-09-04
Post your specs, You might need Alternate CD

---

### Post by Amun11 on 2007-09-04
Ok, I updated the error message in my first post btw, maybe this helps.

It's a Dell Inspiron 6400 (European)

ATI Mobility Radeon X1400
Intel DuoCore T2500
1024 MB RAM (I think DDR400)

More you need to know?

---

### Post by Pumalite on 2007-09-04
That's what I thought; you video card is the problem. You might try this first: at the command line (Ctrl+Alt+F!): sudo dpkg-reconfigure xserver-xorg. Accept most defaults, choose 'vesa' as your driver. Then: startx
Report back.

---

### Post by Amun11 on 2007-09-04
Allright, I dont have time right now, but i'll post as soon as possible.

---

### Post by Amun11 on 2007-09-05
Allright, I've used your info, but it does not seem to work...

first of all, when pressing CTRL+ALT+F1 (you typed F!, I assumed you meant F1) nothing happens...but I figured this has something to do with a command line, so I pressed F6 (Other Options), and typed your code at the end of all the text that was already there (it ended with; "cant remember -- " I typed command here)

When booting it loads something, and then just goes to black (leaves my wifi indicator flickering)...

What is it I'm doing wrong here?

---

