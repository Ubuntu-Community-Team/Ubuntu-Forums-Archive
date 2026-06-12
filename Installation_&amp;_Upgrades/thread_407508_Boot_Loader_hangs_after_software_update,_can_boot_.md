---
title: "Boot Loader hangs after software update, can boot via Recovery Mode"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by Nunnsby on 2007-04-12
Hey all, I hope this is the right area for this post. I hope it is. 

I am running Edgy on my Acer TravelMate 4600. Getting it to run on this laptop was no small feat, as it always hung after booting, well just sat there, but seemed to have loaded everything. I had to use the "emergency shell" to get access to configure the Display Drivers, the ATI PCI Express card I have is the issue it appears. Anyway, I got it installed, and everything was running 100%.

All was working fine and my Grub boot line was: Ubuntu, kernel 2.6.17-10-generic. 

I updated my software according to the software update that was recommended. I just accepted all 203 MBs of it. Haven't used Ubuntu in a few weeks since installing, hence the size of the updates. 

Since the update, there were 2 new lines in Grub: Ubuntu, kernel 2.6.17-11-generic and Ubuntu, kernel 2.6.17-11-generic (recovery mode)

Upon selecting 2.6.7-11-generic the Ubuntu Splash Screen starts up, and then hangs after about 5 secs, half a centimetre, after starting up. The Laptop just sits there and does nothing.

If I reboot into 2.6.17-11-generic (recovery mode ) it boots to a command line prompt. If I type "exit", it continues to boot fine and all works 100%. 

Anyone have any ideas on this? Also, any ideas on how to disable the splash screen, so I can possibly see where it is breaking, add more information on this thread? 

Many thanks

Richard

---

