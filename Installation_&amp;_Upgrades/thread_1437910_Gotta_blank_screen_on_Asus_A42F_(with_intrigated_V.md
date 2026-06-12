---
title: "Gotta blank screen on Asus A42F (with intrigated VGA intel GMA HD, Core i3)"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by ironear on 2010-03-24
I've got a blank screen when try to install Ubuntu 9.04, 9.10, 10.04.
I can't see any GUI.
I tried to run Live CD mode and got the same problem but i heard the logon music sound.Everything look like it's working except the display.

I tried the following methods..
- Press F4 and set to 'Save graphics mode'
- Press F6 to edit 'quite splash' and replace with 'verbose' or 'vga=771'.
- Use an alternate CD when it's install completed i found the black screen again.


HOW CAN I SOLVE THIS PROBLEM???
HELP ME PLEASEEEEE

My laptop spec is ..
ASUS A42F-VX043X 
CPU:Intel Core i3-350M (2.26GHz, 3MB L2 cache) 
RAM:2 GB DDR3 
HDD:320 G 7200 RPM 
VGA:Intel GMA HD Graphics 

Thank you..

---

### Post by rambobear on 2010-03-26
Ironear

I too have the exact same problem!!!

I just bought a Gateway NV59 laptop, with integrated Intell GMA HD; and I am still in the process of trying to install Ubuntu 9.10, 64bit edition, alongside my Win7.

I have read up on a few forums, one of them 

[http://ubuntuforums.org/showthread.php?t=1393413](http://ubuntuforums.org/showthread.php?t=1393413)

and I've tried most of the proccesses they describe, unfortunately they are describing a slightly different video card!

I'm going to keep trying, and anything I find I'll let you know, and any thing you find out would be greatly appreciated as well

Thanks

---

### Post by rambobear on 2010-03-26
Okay so I managed to install Ubuntu 9.10 and get into the operating system; and here's how I did it.

I downloaded the ISO- in my case the "desktop AMD64" edition.

Restarting my computer, I was able to get to the text menu asking "run ubuntu with no changed to..." etc, and upon clicking f6 I edited the boot code:

Where it say quiet/splash, I replaced that with "simple nomodeset" and was able to continue the install.  Right now I am waiting for my downloads to finish with the kernals that should make Ubuntu compatible with Intel's GMA HD

Hope this has helped

---

### Post by ironear on 2010-03-26
Hi,Rambobear
Thankyou very very much for your suggestion.
I use Ubuntu i386 32 bit CDs and solve this problem with your method it's working now.
 
Anyway,I press F4 and select Safe [COLOR=black]graphics[/COLOR] mode.Then I replaced 'quiet splash' with 'nomodeset'.
 
Now working.
 
Thanks again
 
The other useful links
> [http://www.linwik.com/wiki/using+the+intel+arrandale+intel+graphics+media+accelerator+hd+with+ubuntu+9.10](http://www.linwik.com/wiki/using+the+intel+arrandale+intel+graphics+media+accelerator+hd+with+ubuntu+9.10)
[http://intellinuxgraphics.org/2009Q4.html](http://intellinuxgraphics.org/2009Q4.html)
[https://bugs.launchpad.net/ubuntu/+bug/518938](https://bugs.launchpad.net/ubuntu/+bug/518938)


---

