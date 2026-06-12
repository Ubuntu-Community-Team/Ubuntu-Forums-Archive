---
title: "Installation of 7.1 hangs at 83% installing the kernal"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by gkiteguy on 2008-01-22
I downloaded the text version of 7.10 and it seems to install fine until it reaches 83% .
Installing the kernal - retrieving and installing linux generic .....

The system is a 500 MB AMD processor with 384 MB of memory and a 13 GB HD. 

I have tried this on numerous occasions and thought it might be a hardware problem so I put in a smaller hard drive with the same results.  I am a Linux newbee and have reached the end of my tether.  I also tried the live CD update with similar results.  

Any suggestions would be appreciated. 
:(

---

### Post by andrewbrown22 on 2008-02-20
Well, I'm very new to this too, but my install seemed to hang at that 83% mark for some time, but I let it sit and what do you know, it started working after about 5 minutes..  I don't have any explanation for it, but that is what mine did.

---

### Post by nonblock on 2008-04-15
I encountered and investigated this delay on an old machine. The culprits are the update initramfs steps, each of which took about 5.5 minutes. There was an even longer delay for me on "select and install software" for language-pack-en-us. This turned out to be the package template extraction step.

In both cases, you just have to wait it out. But you can follow along if it makes you feel better...

To see what's really going on under the covers with the alternate text install, drop to a busybox console (ALT+F2) and run:

  $ tail -f /var/log/syslog

---

