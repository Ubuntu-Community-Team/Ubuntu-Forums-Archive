---
title: "How to bring my clock to GMT-3?"
date: 2005-09-13
forum: Installation &amp; Upgrades
---

### Post by robertoneto123 on 2005-09-13
Hello,

I install ubuntu about 3 hours ago. It was really good... it detects everything the installation of adicional programs runs quite well. I install gcc, java, and a lot of other stuff. But there is one thing that already gave more trouble that run all the rest of installation: the d... clock.

As a good user, I saw that the clock was wrong. Clicked it with the right button, and "addust date and time" item. I indicated that I am at Sao Paulo/Brazil, and the time on this window works. I closed it, and the taskbar clock was wrong, 3 hours after the real time here.

How do I change it? The settings window give me "11:29", and the taskbar clock "14:29"...

Thanks

---

### Post by joshmachine on 2005-09-13
what do you get if you start a terminal and type "date" at the prompt?

---

### Post by robertoneto123 on 2005-09-13
I got the right time.

---

### Post by joshmachine on 2005-09-13
It seems that the applet doesn't refresh itself well.  It will be correct the next time you log in, and if you want the correct time right now, type "killall gnome-panel" in the terminal. this will force the whole gnome panel to reload and you should see the correct time.

Cheers,
Josh

---

### Post by robertoneto123 on 2005-09-13
Nop and nop...  [-X 

I reboot everything, and the clock shows GMT, not GMT-3...

---

### Post by joshmachine on 2005-09-14
How aggravating.  The strange thing is that the clock applet should be using the same mechanism that the "date" command line program is using to figure what time it is.

First post the following to this thread.

1. The output of the "date" command line.
2. The output of the following typed at the command line "cat /etc/timezone"

The results of the first should include "BRT" in them, and the contents of "timezone" file should be "America/Sao_Paulo"

Try adding a new clock applet somewhere else and see if it is messed up too.  You do this by right clicking on one of the panels and select "Add to Panel" then select "Clock".  If this one shows the right time I would delete the crappy one and add a new one.  

Regardless let me know how it goes, or if the results from the commands listed aren't what were expected.

Cheers,
Josh

---

### Post by goldrush on 2005-09-14
Hi
I am a newbie so the following may not be the correct solution, but had a similar problem.
1. ensure you have selected the correct timezone as sudo under Admin.
Open select time servers. Deselect ubuntu and select a local time server from the list (or add your local server URL)

2. If this shows correct time, but your "clock" at top left  shows differently, Open clock icon (top left of screen) and de-select use UTC.
(Just noticed you stated that it showed GMT, not GMT-3// in which case SELECT use UTC)

However, whilst this sorted out Ubuntu, and is ok on ubuntu reboot, now whenever I boot into windowzy the clock is incorrect. Ubuntu must incorectly set the harware clock?
Hope it helps

---

### Post by robertoneto123 on 2005-09-16
[QUOTE=goldrush]
2. If this shows correct time, but your "clock" at top left  shows differently, Open clock icon (top left of screen) and de-select use UTC.
(Just noticed you stated that it showed GMT, not GMT-3// in which case SELECT use UTC)[/QUOTE]

Thanks, that's the trick! It works fine now.

---

