---
title: "Problem Installing ubuntu on dell dimension xps gen 5"
date: 2005-11-17
forum: Installation &amp; Upgrades
---

### Post by astro2990 on 2005-11-17
Hello all

I am trying to install ubuntu version 5.10 on my dell dimension xps gen 5. I get to the part where ubuntu is trying to load components from the CDROM. It chokes and gives an error message about not being able to read from the CDROM. At first I figured it was a bad burn, so I tried burning several CD's, same problem. Then I ordered the pressed CD's, and it still chokes on exactly the same spot. I have tried telling it to abort that step, and then go back to the step where it loads info about the CDROM from the pool, and now that step fails too. When things fail, my CDROM drive is spinning at high velocity, and is making a loud humming sound, and I can't eject the disc from the drive by pressing the button as an attempt to reset things (I have no idea if this is relevant or not, but I thought I should mention it). Has anyone encountered a similar problem? Any suggestions on how to solve the problem?

---

### Post by yesplease on 2005-11-17
Perhaps this helps (it is an old thread though) [http://ubuntuforums.org/showthread.php?t=15708&highlight=install+dma+cdrom](http://ubuntuforums.org/showthread.php?t=15708&highlight=install+dma+cdrom)

---

### Post by Chayak on 2005-11-17
I had a similar problem installing on a friends XPS.  It worked for me when I used ```
linux ide=nodma
``` Hope this helps.

---

### Post by yesplease on 2005-11-17
Edit: @chayak, that is what the thread in the link above recommends :) I think it is a strange solution because after a regular install DMA is off by default. Is it on by default during install?  I dont understand this, but it is good that is a solution for some people.

---

### Post by astro2990 on 2005-11-18
I tried that, but it didn't work. I appreciate the help. Any other ideas?

---

### Post by SPENEN on 2005-11-18
I have the exact same problem, and I've tried the things posted in this thread.

---

