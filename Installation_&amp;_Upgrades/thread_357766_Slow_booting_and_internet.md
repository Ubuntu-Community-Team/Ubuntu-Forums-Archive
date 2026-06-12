---
title: "Slow booting and internet"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by ChameleonDave on 2007-02-10
I am fairly experienced with PCLinuxOS and Puppy Linux (plus Windows, like virtually everyone).

I downloaded the ISO for Ubuntu 6.10 "Edgy Eft" and installed from the LiveCD.  

I set up a triple boot system (or quadruple if you consider my bootable Puppy Linux thumbdrive).  The first thing I noticed was that the Internet connection ran noticeably slower with Ubuntu than with my other three operating systems.

I needed to install some extra stuff, and get some updates.  So, I opened Synaptic and installed a large amount of stuff, such as all of KDE, allowing me to choose between Gnome and KDE at log-in.  I also installed all the updates/upgrades that came up.  I did this is several waves, because of the quantity of stuff to download.  

I'm not sure at what point it happened exactly, but booting Ubuntu started to go very slowly.  It seems to perform some massive tasks and checks (not filesystem checks though) that make the whole thing take about ten minutes.  Presumably this is logged somewhere, so I'll post the logs if you tell me where to look.

So there are the two problems: slow internet from the beginning, and slow bootup since installation/updating of software.

Can anyone offer some help?

---

### Post by ingo on 2007-02-11
> cat /var/log/messages|less
will give you a pure, unadulterated log. 
> dmesg
is another one telling you what the machine has been up to.

One hint on how to speed up booting: uncomment any unneeded interfaces from your /etc/network/interfaces

hth

---

### Post by ChameleonDave on 2007-02-11
OK, here's an attachment.

---

