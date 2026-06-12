---
title: "Ubuntu 11.04 install problem"
date: 2011-06-23
forum: Installation &amp; Upgrades
---

### Post by dgundling on 2011-06-23
I have my hard disk divided into 3 primary partitions. The first has WIN98SE, the second has Ubuntu 10.10, and for the third I am attempting Ubuntu 11.04 since, with my wireless network, the 10.10 to 11.04 upgrade failed due to dropped connection. 
 
Re installed 10.10 and it seems to work fine. (I have had Ubuntu for about a month.) 
 
I downloaded and created a CD for 11.04 and ran it to install 11.04 on my third partition. It seemed to go in OK but it won't run. I get a bit of a window here and another bit of window in another place on the single monitor screen. It told me I did not meet the hardware requirements for Unity and to go back to the classic at the log in prompt. There is a mild problem in that when I boot 11.04 I don't get a log in prompt. Should I reinsall over what I have or wipe the partition and start the install over again? Power off is the only way to shut down as trying to open a tool bar item fails in that the opened screen closses immediately if not sooner.
 
The grub screen on boot up show all 3 OS for selection. I can run 10.10 after the attempted install of 11.04.
 
What would be my best approach?
 
Thanks.
 
Dave

---

### Post by dgundling on 2011-06-24
Continuation of my original post. I did a reinstall of 11.04 over my first 11.04 installation. The only thing I changed was to require a password for access. For the original installation a paaword was not required for access to 11.04.
 
Still no good. It boots to what looks like the classic screen. (Very similar to my 10.10 installation.) Tried to fix the date and time. Date/time screen came up but could do nothing with it. In the course of playing around on the date/time screen, the trash screen came up unasked. It lay over the date/time screen and could not be moved or shut down. The only way I was able to shut down was with a power off. 
 
BTW, grub works fine. On boot up it shows all three OS that I on the hard disk and I can reach any of them.
 
Ideas or solutions please.
 
Thanks.
 
Dave

---

### Post by Dry Lips on 2011-06-24
> **dgundling said:**
> Continuation of my original post. I did a reinstall of 11.04 over my first 11.04 installation. The only thing I changed was to require a password for access. For the original installation a paaword was not required for access to 11.04.
 
Still no good. It boots to what looks like the classic screen. (Very similar to my 10.10 installation.) Tried to fix the date and time. Date/time screen came up but could do nothing with it. In the course of playing around on the date/time screen, the trash screen came up unasked. It lay over the date/time screen and could not be moved or shut down. The only way I was able to shut down was with a power off. 
 
BTW, grub works fine. On boot up it shows all three OS that I on the hard disk and I can reach any of them.
 
Ideas or solutions please.
 
Thanks.
 
Dave

Hmmm... I'm not sure what your problem is? Is it that you're unable to run Unity?
Perhaps you could post a couple of screen-shots in order to explain what the problem
is?

---

### Post by dgundling on 2011-06-24
Dry Lips,
 
Thanks for the reply. I think I have solved the problem. I received the Official Ubuntu book today. It spelled out the installation process. When the log in screen appeared I needed to click on my name and that brought up a tool bar at the bottom of the screen. Per the book, I selected the classic desktop. (the one that was second in the list, I forget the exact name) then evrything worked fine. The basic problem was that the distro provided no information on this portion of the install process. New guys like me don't know it and therefore have problems. Perhaps, in the future, distros need to start out with a read me file explaining any actions needed to be taken?
 
Incidentally, on my first install attempt I selected that no log in was needed. It came back and said my hardware did not support Unity. Turns out my mother board was too old. Going the route of asking for log in bypassed that issue.
 
Dave

---

### Post by Dry Lips on 2011-06-25
Ok! Now I see. Yeah, easy stuff can be difficult when you just don't
have a clue about what to do! Trust me, I know, I'm quite new to Linux
as well...

Enjoy your Ubuntu, I hope you'll stick around!

---

