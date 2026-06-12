---
title: "Studio install issue"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by tech4 on 2008-06-20
Hello all,

I did a fresh install of Hardy Heron then I downloaded the DVD image of Studio and ran that. After it doing it's thing and rebooted I had no changes. So, I decided to go into terminal and do it the old way and now I get this when I run "apt-get install" on any studio package,

Media change: please insert the disc labeled
 'Ubuntu-Studio 8.04 _Hardy Heron_ - Release i386 (20080423.1)'
in the drive '/cdrom/' and press enter

I am not sure what is referring to. I put the DVD in the drive but I get stuck in this loop. I'm not sure how to get around this. I looked but found nobody with this issue. I am stuck.

---

### Post by avtolle on 2008-06-20
I'm not familiar with Ubuntu Studio, thus I'm a bit confused with your post. Did you install 8.04 Ubuntu and then Ubuntu Studio on different partitions? Or, did you install Studio on top of the 8.04 in the same partition? 

The bit I read from the Ubuntu Studio website implies, at the very least, that the DVD contains the OS, etc. for installation. Thus, my questions.

---

### Post by tech4 on 2008-06-23
Sorry, Ubuntu studio is a package you can install on-top of Ubuntu. It includes a bunch of audio/video apps. I found that I'm not the only one with the issue.

---

### Post by Bucky Ball on 2008-07-17
Uh-uh. No. If you had Ubuntu loaded, you should have just loaded Studio apps, themes, desktop etc through synaptic and repositories. Loading over the top could cause some confusion, installing same OS twice, as Ubuntu Studio 8.04 is Ubuntu 8.04(!) with its own (extra - notice UStudio is a larger ISO) set of packages and apps.

You should definitely install these OSs on seperate partitions or go the Synaptics or terminal route (enable the Ubuntu Studio repository - this way it will see what is already there and not attempt to install, only installing its extra customisations). 

This will help;

[http://ubuntuforums.org/showthread.php?t=794423&highlight=64+studio](http://ubuntuforums.org/showthread.php?t=794423&highlight=64+studio)

Good luck.

---

