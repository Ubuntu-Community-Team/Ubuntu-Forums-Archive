---
title: "Graphics problem during installation"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by zerglin on 2007-12-04
I have a Dell Inspiron 6400, with an ATI X1400 graphics card. I'm trying to install Ubuntu 7.10 using a live cd, but as the install initiates and starts performing tests at some point the screen starts to twitch and some corrupted graphics come up. After a while a message pops up saying: "The display server has been shut down about 6 times in the last 90 seconds. It is likely something bad is going on. Waiting 2 minutes before turning on display :O ". After two minutes the process repeats itself.
Any ideas of what is wrong?

Thank you,

---

### Post by Pumalite on 2007-12-04
You have to install with the Alternate CD and configure your xserver at the end of the installation. Come back after you finished the installation.

---

### Post by zerglin on 2007-12-04
Forgot to mention that i'm trying to install as dual boot on windows vista

---

### Post by Pumalite on 2007-12-04
Then, don't forget to allocate space for Ubuntu FROM Vista first.

---

### Post by zerglin on 2007-12-04
> **Pumalite said:**
> Then, don't forget to allocate space for Ubuntu FROM Vista first.

By that you mean create the partition from Vista first?
In addition to that, i have read in other posts that there is a problem if you have many partitions, so given that there are already 4 partitions on my drive for some reason (blame DELL) i should delete 2 of them?

Thanks,

---

### Post by Pumalite on 2007-12-04
If you have 4 primary partitions, you have to create an extended partition out of one of them and in that extended partition Ubuntu will create the logical partitions that it needs.

---

### Post by zerglin on 2007-12-07
Finally finished installing. However after a series of changing resolution settings for my laptop monitor and my external display Samsung SyncMaster 940BW, I started getting the same error I got during installation and now i can't log into Ubuntu even on low-graphics.

Any ideas?

Thank you,

---

