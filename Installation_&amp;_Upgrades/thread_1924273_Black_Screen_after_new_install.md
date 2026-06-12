---
title: "Black Screen after new install"
date: 2012-02-12
forum: Installation &amp; Upgrades
---

### Post by DIYgirl on 2012-02-12
Completely new to linux.  Was hoping to find some help or maybe pointed to a thread to help.   

I built a new system from scratch: antec 750w power supply, gigabyte GA-Z68X-UD3h-B3 mobo, Intel i5, No graphics card, 2tb hard drive.  Older LCD monitor. also I am connected to the internet (no wifi yet).

I loaded Ubuntu 11.10 (64 bit) using a CD, got the black screen and followed the instructions in:
 
[http://thedaneshproject.com/posts/ubuntu-11-04-blank-screen-on-boot-solved/](http://thedaneshproject.com/posts/ubuntu-11-04-blank-screen-on-boot-solved/)

under NOMODESET - i checked under system -administration - additional drivers and found none.  I installed ubuntu on the hard drive and now I continue to get a loading operating system message followed by the black screen.  What now?

Do I need to get the windows drivers for the onboard graphics processor on the motherboard? How do I do this?  since running off the cd is the only way to get the o/s to work but then it will not save changes to the HD, right?

Will changes to Plymouth or non graphical boot do the trick?  Will I lose out on some capabilities if I decide to get a new monitor after making these changes?

I am able to load off of CD and pull up GRUB but am lost at this point.

Thanks for the help and apologies if this is already solved elsewhere.  I could not find what I needed.

---

### Post by 2F4U on 2012-02-12
Windows drivers do not work on Linux. Did you try the nomodeset option on the installed system? You can add the option in the grub boot screen. Chances are that if it worked on the liveCD it will also work on the installed system.
What make and model is the onboard graphics card?

---

### Post by DIYgirl on 2012-02-12
resolved this with the Boot Fix program Thanks!

---

