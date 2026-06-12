---
title: "A couple of questions"
date: 2008-09-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by cariboo on 2008-09-25
1. Has anybody noticed that the alpha 6 livecd doesn't create /usr/local/bin? I went to copy some scripts that I normally use from my scripts directory to /usr/local/bin and was told that that directory didn't exist, I tried to cd into it and got the same message. I cd'd into /usr/local, and sure enough there was no bin directory. I installed from the alternate cd when it came out and the directory definitely was there.

2. What is the difference between the alternate cd and the livecd, I have installed alpha 6 from both and with the alternate cd everything installed exactly the way it should, my hdd's were detected in the proper order. Once X had started I selected the restricted nvidia drivers, they downloaded right away. With the livecd my hard drives were detected in the wrong order and upon reboot I had to edit grub to point to the drive before it would boot. Once X started It did ask me to install the restricted nvidia drivers, but I had to update my sources list before the drivers would download.

Using the alternate cd the extra keys on my Microsoft Natural 4000 keyboard worked right out of the box, with the livecd the extra keys don't work.

Sound worked right away with the alternate cd, but didn't work with the livecd until updates were installed.

It looks like the two different methods of installation are two separate projects, instead of one install cd with or without a gui.

Jim

---

### Post by Nullack on 2008-09-25
Ubiquity uses different mechanisms in the livecd install.

Please consider bug reports my friend :)

---

### Post by RAOF on 2008-09-25
Although I'm not sure (although I could be wrong) that lack of /usr/local/bin is actually a bug.  No Ubuntu package should ever touch anything under /usr/local during install.

---

