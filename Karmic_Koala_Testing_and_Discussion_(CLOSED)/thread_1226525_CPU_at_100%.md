---
title: "CPU at 100%"
date: 2009-07-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tjeremiah on 2009-07-29
I first notice this when I updated this morning and also noticing the fan on my laptop never shutoff. I have no idea what is causing it. Tell me what to put in the terminal, etc so more details can be provided. Below is a pic.

---

### Post by wayne_cat on 2009-07-29
open a terminal and run top

---

### Post by tekstr1der on 2009-07-29
This happens to me as well as of today's power related updates. The culprit was gnome-do @100% CPU upon boot. Killing it off and relaunching it works fine for now.

---

### Post by W4l0ck on 2009-07-29
Try restarting all your applications.

---

### Post by llamabr on 2009-07-29
> **W4l0ck said:**
> Try restarting all your applications.

That's not really very practical advice, nor is it very helpful.  What's the difference between rebooting, and restarting ALL of your applications?

Instead, open 

```
top
```

in a terminal, and find the application that's using all of your cpu.  Post back the results, as often this is something you intended, rather than some problem.

---

### Post by psyke83 on 2009-07-29
Also, gnome-system-monitor itself can cause high CPU due to the graphical components, especially (but not exclusively) if using an older graphics card.

Never rely on the information from that application - use top as suggested.

---

### Post by Podex on 2009-07-30
You can also install and use htop instead of top. It has a slightly nicer and useful interface :) You can actually select running processes in it and kill them.

---

### Post by poppo_g on 2009-07-30
I have the same issue. It's caused by Firefox 3.5.1. Anyone got a solution for this?

---

### Post by danxx on 2009-07-30
read this

[http://ubuntuforums.org/showthread.php?t=833608](http://ubuntuforums.org/showthread.php?t=833608)

---

### Post by poppo_g on 2009-07-30
Thanks, i will look into this

---

### Post by benjamimgois on 2009-07-30
I have the same problem. When i finish booting my machine the CPU stays in 100%, so i have to make a CTRL + ALT + BACKSPACE, and log on the system again. Than everything back to normal. I'm using the Xorg-edges PPA, so i think that the problem can be with a unstable version of X or intel-drivers. Anyone here have the same problem using the original stack  ?

---

