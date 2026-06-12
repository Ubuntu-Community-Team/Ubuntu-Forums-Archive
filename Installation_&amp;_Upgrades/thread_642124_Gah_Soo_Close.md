---
title: "Gah Soo Close"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by Dan221081 on 2007-12-16
Hi I am yet another user that appears to be having problems with ATI cards and their drivers. I wil try to keep this as short as possible and to the point as possible.

Everytime i try and setup linux I seem to hit brick wall problems to then discover that a lot of other people have had and after wasting hours apon hours trying tofix it I end up giving up and going back to using windows.

This time I am determined to not let that happen well the last bit anyway ( I already worked through the night / morning last night trying to get it sorted) 

The main problem or the most obvious one that I did have was that when I tried to install Ubuntu (desktop verison) was that it just went to a black screen in the install !!! That wasn't a good start to be honest and almost made me stay well clear... However a quick search and this was revealed to be a common problem and the solution was to install from the alternative cd which I did. 

The next problem was that when it had finished installing and I restarted the machine it did the same black screen thing. However after a lot of messing around and trying things and searching online I found that if I pressed control and alt and F1 I would get the console back again. Further more if after doing that I pressed Control and alt and F7 I got the Gui come up...

However having to do that every time you boot is a tad on the rubbish side so I looked into what might be causing it and saw that it was just using the HAL driver and not the fglrx one. When I tried to tick that box it wouldn't let me so I did loads more searching and then found that someone did a complete reinstall with a internet connection and this seemed to solve the issue. Rather than using a sledge hammer to kill a fly I decided to connect the machine up to the internet and update it. 

After doing the update and restarting I tried to do the same thing tick the box with the other driver listed and low and behold it prompted me to install the standard installation cd and effectively installed the driver and ticked the box. Sorted I thought..... but no the problems had just started the black screen issue still existed and now I was limited to 800 x 600 or 640 by 480..

I have tried several things since like trying to change the monitor type to generic 1024 x 768. Which then gives me the option of the higher resolution but then runs like a dog. 

I have managed to get it to the stage where it is entering the gui without any prompting but it is entering it now in "low graphics mode" and its prompting me to configure it.

when I look at the config file in /etc/X11/ it lists all the modes that the graphics card can display and all the modes that the monitor can display yet when you look at the list through the gui (screen resolutions) it appears there are only 2 modes available (800 x 600 or 640 by 480)

So this is my last frail attempt at getting this sorted before I completely give up on wasting time with any form of linux. Shame really because it seems to have detected my wireless card yet made the mistake of not supporting one of the most common graphics cards out there.

System Specs 
P4 2.4 Ghz 
1 Gb RAM
120gb HD
Radeon 9800pro
Samsung 172x 17inch LCD monitor

---

### Post by viking777 on 2007-12-16
Computers are funny aren't they. I always get that 800x600 nonsense every time I try to install Suse linux, but never with Ubuntu (I have a Radeon mobility x1600).

Anyway if you want a proper driver for your card, you take your little 800x600 window, connect to the internet and go here:

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

Make the appropriate selections, and it will present you with the appropriate driver for you to download. 

Then go here:

[http://www.amd-firefly.com/firefly2007/fireflyclient.jsp?loadServiceID=145615e10ce83cdae9-7ff9&loadLocationID=68bffad5112ba80974e-4000&loadDesignID=14114cf4d511422483ae1-2a5d&loadSubmissionType=requestStart&loadTemplateID=](http://www.amd-firefly.com/firefly2007/fireflyclient.jsp?loadServiceID=145615e10ce83cdae9-7ff9&loadLocationID=68bffad5112ba80974e-4000&loadDesignID=14114cf4d511422483ae1-2a5d&loadSubmissionType=requestStart&loadTemplateID=)
 
to find out how to install it.

---

