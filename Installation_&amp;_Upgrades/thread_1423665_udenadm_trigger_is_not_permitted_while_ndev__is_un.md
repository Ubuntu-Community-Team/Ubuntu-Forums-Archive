---
title: "udenadm trigger is not permitted while ndev  is unconfigured"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by apachemaven on 2010-03-06
HI:
Last night, when I update the ubuntu, I set it shutdown after 60 minutes uisng "sudo shutdown 60",because I think the update will complete in 40 minute.
However today when I start the computer, it can not startup the ubuntu.
I got a screen which sown the message in the title,after I search it using google, some people have encounted this proble, their solve way is to use a live cd to chroot to the old root and complete the update.
However I can not.
The following is my suitation:

[http://imagebin.org/87841](http://imagebin.org/87841)  my  command


[http://imagebin.org/87840](http://imagebin.org/87840) my partition
 
SO, how to do now? I am in hurry, I hope some one can do me a favor.
Thanks.

---

### Post by falconindy on 2010-03-06
Not sure why you stopped. If you notice in your first screenshot, after the 'chroot' command, you're apparently in the root directory (/) after being in home (~). This means the chroot was successful, despite a few errors. The mounts you've created were all successful.

Keep going.

---

### Post by apachemaven on 2010-03-07
> **falconindy said:**
> Not sure why you stopped. If you notice in your first screenshot, after the 'chroot' command, you're apparently in the root directory (/) after being in home (~). This means the chroot was successful, despite a few errors. The mounts you've created were all successful.

Keep going.
god!! You mean I have enter the root I mounted?

---

