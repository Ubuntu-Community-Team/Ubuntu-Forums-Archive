---
title: "[SOLVED] Does it affect an ubuntu if i changed all my hardware on a PC to a new one.."
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by house7 on 2008-04-19
Greetings.

on a couple days i will replaced all my hardware inside my PC (Motherboard, Processor, RAM, VGA card) except my Hard Disk Drive. I currently have dual boots installed nicely. And what i'm asking is..

Does this upgrades will affect my ubuntu or other OS? Some errors will occur or anything? because i'm really noob on this. :)

I'm kinda nervous about this.. Please leave an answer or suggestions. Thank you so much..

---

### Post by christianxxx on 2008-04-19
> **house7 said:**
> 
Does this upgrades will affect my ubuntu or other OS? Some errors will occur or anything? because i'm really noob on this. :)


I haven't tried on linux, but I know at least widows hates it. But it's usually just to install the correct drivers, but it's a mess for a while.

---

### Post by Rocket2DMn on 2008-04-19
This will cause problems, esp. if there is a major difference in hardware.  It would probably be best to do a fresh install with the new hardware.
All sorts of problems can result from swapping hardware.  It might be workable, but you might have to do a lot of troubleshooting.  If you choose to try, please make sure you have everything backed up.

---

### Post by 3rdalbum on 2008-04-19
If you are running the proprietary Nvidia driver, and are going to switch to a non-Nvidia graphics card, then you should change the driver in "Screens and Graphics" to "vesa" before changing the hardware. Same goes for the opposite direction (e.g. if you have ATi currently and are switching to Nvidia).

---

### Post by Linux&amp;Gsus on 2008-04-19
RAM usually doesn't matter. 
The Video card can will be reconfigured at first boot. I did that once with Kubuntu, the OS recognized the new card asked me if I want to configure it now, and all was fine. On Windows you simply need to install the new drivers that are coming with the card and most likely reboot and all is fine.
Motherboard and Processor, well, don't quote me on this I'm no expert really and I never did it with Linux. But on Windows I didn't had any success. In other words, when ever I upgraded the processor or motherboard I had to re-install Windows. However that might have changed in the days of XP and Vista, I dunno. At least I've never been able to do it. But that should not mean that it's impossible.

Cheers,
Steve

---

### Post by house7 on 2008-04-19
> **Linux&Gsus said:**
> RAM usually doesn't matter. 
The Video card can will be reconfigured at first boot. I did that once with Kubuntu, the OS recognized the new card asked me if I want to configure it now, and all was fine. On Windows you simply need to install the new drivers that are coming with the card and most likely reboot and all is fine.
Motherboard and Processor, well, don't quote me on this I'm no expert really and I never did it with Linux. But on Windows I didn't had any success. In other words, when ever I upgraded the processor or motherboard I had to re-install Windows. However that might have changed in the days of XP and Vista, I dunno. At least I've never been able to do it. But that should not mean that it's impossible.

Cheers,
Steve


Wow really thanks for the quick responses. I agree with you, RAM really doesn't matter, just installed one. But this is a major upgrade and  I think i will do a fresh install and move on (oo i'm gonna spend some time with this though :) ).. 

thank you for your suggestions and advice...

---

### Post by pbpersson on 2008-04-19
I once swapped out the motherboard on an XP machine, keeping all other hardware the same - the OS went totally belly up on me.

I had to boot into safe mode and in device manager uninstall everything related to the motherboard - I am talking hard drive controlller, floppy controller, USB controller, etc.

Then when I booted into regular mode, XP recognized and installed everything it needed from the I386 directory.  Windows was about 95% there but still used to blue screen sometimes, especially at shutdown.  That was fixed when I did a fresh install of Windows.

---

### Post by Linux&amp;Gsus on 2008-04-19
Fresh install is probably a good idea. Make a good backup of your data, or while you get a new system anyways, get a new HD and install there. Then transfer the data from the old one and use that HD as backup drive, e.g. buy an external case for it, if you haven't already a backup solution like that.
Or well, leave everything as is and get a new case as well, basically a completely new box, install, transfer the data and use the old as test box or server.

Oh well, you have plenty of options...
Have fun rockin' the house.
:guitar:

---

### Post by fain on 2008-04-19
Ive done this before a few different times. Each time a different result. Vista will complain that you have changed your hardware and make you call microsoft to re activate always. Nothing like making your customer feel like a criminal.

Ubuntu should boot right up but its a touchy situation. It really depends on a lot of things. 

Make a back up and try it if not o well you haven't lost anything.

---

