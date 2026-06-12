---
title: "I need help compiling a vanilla kernel in Ubuntu 7.10"
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by Sims2789 on 2007-12-12
I want to compile a vanilla kernel in Ubuntu 7.10. I've never compiled a kernel before, and am not a superuser, so understand that my level of experience and computer knowledge isn't nearly as high as the typical "technical" Linux user of five years ago.

Therefore, telling me what to do (as in "load the right modules, then use the command line to tell it to compile") won't really help me; I need step-by-step instructions. I've searched online and only found Ubuntu 6.10 instructions that meet my level of experience, and they included the rm command so I didn't want to risk removing something in 7.10 when I wasn't sure it would work.

Also, is it possible to save a custom vanilla kernel to a CD in case I need to reformat my hard drive?

---

### Post by Sims2789 on 2007-12-12
bump

---

### Post by MeathooK427 on 2007-12-12
Have you checked out the "Master Kernel Thread" here on this site?

---

### Post by Sims2789 on 2007-12-12
Thanks soooo much. This is exactly what I needed. So far so good! :thumbsup:

In case anyone found this page from a search engine, and step one fails: For some reason I already had libncurses5 and libncurses5-dev so I had to remove "wget -c libncurses5 libncurses5-dev" from step 1. If you have the same problem check in Synaptic if you have some of the programs already.

---

### Post by Sims2789 on 2007-12-12
Wait, will I still be able to boot from my old kernel? I'm mainly doing this to have a vanilla kernel in addition to my Ubuntu one and to remove unnecessary drivers and such.

---

### Post by Keyper7 on 2007-12-12
Yes you will. If you follow the instructions correctly, you'll gain a new entry on your GRUB menu and will be able to boot the old kernel any time you want.

---

### Post by MeathooK427 on 2007-12-13
Also, don't take out that whole bit of code you mentioned, just the "-c" part after wget. It'll work like a charm. Good luck! I'm currently having problems upgrading the kernel on my Gutsy install...annoying....

---

