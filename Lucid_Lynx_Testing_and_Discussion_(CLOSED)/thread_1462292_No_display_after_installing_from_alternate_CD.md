---
title: "No display after installing from alternate CD"
date: 2010-04-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lduperval on 2010-04-25
Hi,

I just installed RC1 from the alternate CD and when I boot the system normally, it hangs somewhere in the process and I am unable to determine where because I see nothing on the display. Even switching to a terminal does nothing.

I tried rebooting in failsafe mode, and that worked. When I did though, it asked me if I wanted to run in low graphics mode, and I replied yes.

To my surprise, low graphics mode turns out to be 1024x768 which is the highest resolution of my old Intel card. It displays correctly so the problem seems to lie elsewhere.

What are my options at this point? Is there a mode that allows me to run the boot sequence event by event, and to be asked first if I want to execute something?

Thanks,

L

---

### Post by lduperval on 2010-04-25
I quickly browsed a thread on Plymouth. Maybe my problem is related: I see the spash screen show up (where it says "Ubuntu") and then things go black and never come back.

L

---

### Post by lduperval on 2010-04-25
The problem is definitely X running in normal mode. I started with the "console" option in GRUB and then launched X with startx. When I did, the screen became blank and that's it. Nothing else.

I can't even do a  Ctrl-Alt-F1 or anything to get access to a console. The only thing that seems to work is a hard reset, i.e. turn the laptop off completely.

Next step is to get ssh going on this and try to log in remotely when it is frozen to see what the log files say.

Any tips appreciated in the meantime,

L

---

### Post by lduperval on 2010-04-25
Oh, and might I add that whenever I log in with failsafe mode, I always get a popup saying that the Power Manager couldn't be stopped. I have to select "Logut Anyway" (???) to keep going.

L

---

