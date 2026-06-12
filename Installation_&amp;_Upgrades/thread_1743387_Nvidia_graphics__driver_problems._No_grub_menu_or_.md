---
title: "Nvidia graphics / driver problems. No grub menu or teminal"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by grants on 2011-04-29
Here is a small summary of what I've done. 

Old graphics card . . . . ATI Readon x700
New graphics card . . . . Nvidia 9800gt
Newest graphics card  . . Nvidia GTX 560ti

ATI card will work all the time. 

Nvidia Cards will not let me install the developer driver from the Nvidia site. 

Default configuration works for the nvidia cards but this is not what I want to use. I need to install Cuda toolkit and need the source drivers to get it to work. 

While booting up I see my motherboard boot screen, I see the grub menu (finally after modifying the grub configuration file). Default display drivers seem to work and I get to the desktop. 

Problem 1:
CTRL ALT F1 to bring up terminal and exit out of desktop I just get a blank screen. 

I've been able to get ssh access so I can quit gdm and modify the boot black list so I can install the driver but i still get some errors.

Problem 2: 
After driver install (forces xorg configuration) and reboot I get an error saying the drivers can't be found and I can only run in low graphics mode or a few other options like exit to terminal. 

I choose exit to terminal and get a blank screen. 

Ultimately I'd like to be able to install the Nvidia dev drivers and Cuda Toolkit for my card but why wouldn't I be able to see the terminal when exiting gdm? 

If this is the wrong location for this post. Please be nice and point me in the right direction.

---

### Post by grants on 2011-04-29
re installation gives me an error saying x server is running. Well it isn't i'm in terminal and sudo gdm stop doesn't seem to do anything.

---

### Post by grants on 2011-04-29
Work around for the above error is to ps aux | egrep 'gdm|xorg|xserv'

and kill -9 all the pid's 

After this I get a new error saying that 
"unable to load the kernal module 'nvidia.ko'"

Google search doesn't help witht nvidia.ko

---

### Post by grants on 2011-04-29
I seem to be stuck trying to figure out why Nvidia.ko can't be found. 

Please Help. . .

---

### Post by grants on 2011-04-30
Anyone?

---

### Post by Logan7x3 on 2011-04-30
It would be a good idea to boot off of a LiveCD, go to additional drivers, then see what you find. 

thats all that i can think of! Hope it helps in any way!

---

### Post by MAFoElffen on 2011-04-30
[FONT=Arial Narrow]I did this during testing... Had to get help from[/FONT] **cariboo907 **to do it...[FONT=Arial Narrow]As I remember he had me unistall nouveau before installing the proprietary drivers.[/FONT][FONT=Arial Narrow] The other drivers did not show up until I did that.  I ended up having to go on and test other things but...

I wish he would notice this thread... so he could explain what he had me do.  I found the dev thread where that happened... it was from here on:
[http://ubuntuforums.org/showpost.php?p=10662095&postcount=5](http://ubuntuforums.org/showpost.php?p=10662095&postcount=5)

And from there- show full thread from that post.  There was also a full nVidia Test Section refrenced from the natty dev area, but it went away when they closed that area Thursday... 

Hope this is of some help.
[/FONT]

---

### Post by grants on 2011-05-01
I found this thread. . .

[http://ubuntuforums.org/showthread.php?t=1473045](http://ubuntuforums.org/showthread.php?t=1473045)

Sounds like a similar problem I'm having. I'll try some of this and report back but I'm not trying to install the Ubuntu additional drives. I'm trying to install cuda drivers and cuda toolkit.

---

