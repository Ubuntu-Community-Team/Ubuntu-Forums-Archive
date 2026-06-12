---
title: "CPU fan races at idle"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by angler on 2006-11-02
I did a clean install of edgy and have a strange fan issue i never had with dapper d. The fan speed is variable during different tasks as I would expect, but if I walk away and come back, the fan is running full throttle. I can't imagine it's bad for the cpu, but it has to be hard on the fan, and it's annoying because my fan is pretty loud.
I have tried letting it go idle with no applications running... same thing.
I have left nicotine and ktorrent doing what they do... same thing.
I have turned off the screensaver... same thing.
I just can't pin down the problem and suspect its a kernel thing.
I'm a recent windoze convertee so I've done what I can, including trying to setup lm-sensors, but I get the same error mentioned in this post- [http://www.ubuntuforums.org/showthread.php?t=288448&highlight=sensors+fan](http://www.ubuntuforums.org/showthread.php?t=288448&highlight=sensors+fan)  I installed KSensors which is useless but interesting that it works in relation to that other thread. I guess I'll try conky and see if I can get some numbers to see just how hard the fan is running. Any help is greatly appreciated - otherwise, I might be going back to dapper...bummer.
Box= U. Edgy 6.10 Intel board P4 (519) 3.06 gHz SATA disks 512 DDR

---

### Post by cephlon on 2007-04-30
Did you ever find a solution for this? 
As soon as my laptop goes into screensaver mode, the Fan goes full blast and will stay like that all night. Its super annoying and I am sure I'll burn out the fan a lot sooner. Is there any way to reduce the fan usage during screensaver mode?

---

### Post by Redeyes_Gambit on 2007-04-30
Angler's problem and your problem are slightly different Cephlon. Angler says that the fan will blow constantly, screen saver or no. You say your fan goes full blast when the screen saver is active (unless I misunderstood, in which case I would be happy to be corrected :-)

What screen saver are you using? is it a GL-based screen saver? Do you have hardware acceleration-enabled drivers installed for your graphics card?

---

### Post by cephlon on 2007-05-01
Yea, you could be right. I just thought it might be similar because he said the fan goes full blast when his computer is idle. 

I have tried all different kinds of screensavers, but even on blank, the fan turns all the way up. The screensaver goes away and the screens turn off after 15 mins, but the fan is still going. Also, all the screensavers work fine. 

How do I check the drivers?

---

### Post by Redeyes_Gambit on 2007-05-02
Well, unless you installed the official Nvidia drivers yourself, chances are you are using the "nv" driver, which will give you full resolution, but no hardware acceleration for graphics.

(Unless of course you are using Feisty. I don't know if the Ubuntu guys finally got permission to include the official Nvidia drivers or not in Feisty.)

If you do not have official Nvidia drivers installed then any openGL based screensavers (and any others that need hardware acceleration) will be using software acceleration instead of hardware. This, in essence, offloads all of the work that would normally be done by the graphics card to the processor, causing it to heat up, and trigger a fast spinning fan.

There is probably a command that will output exactly what driver you are using, I just don't happen to know it. Maybe someone else could help us out there.

---

