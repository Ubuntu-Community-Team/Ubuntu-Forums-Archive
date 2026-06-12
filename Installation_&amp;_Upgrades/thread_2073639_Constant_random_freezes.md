---
title: "Constant random freezes"
date: 2012-10-20
forum: Installation &amp; Upgrades
---

### Post by hexg on 2012-10-20
Sorry for the dumb question in advance.

I have been trying to get Ubuntu to work on my machine for almost 2 months now. I've tried almost every Ubuntu-based distro out there and all of them freeze at completely random times.
When I managed to install it on my hard drive without it freezing mid-install it still froze constantly when using it. I've got no idea what the issue is or how to fix it but all I know is that the mouse doesn't move at all and ctrl+alt+f2 doesn't do anything while it's frozen.

I doubt it's my graphics card or CPU overheating because I can run them at very hot temperatures without any glitches or freezes on Windows.

If anyone could help me I would be extremely appreciative. This issue has been frustrating me for so long and I hate to join a forum just to ask for support but no one else seems to have this issue, and the Ubuntu community is known to be really helpful and nice compared to other Linux communities.

My hardware specs:

[B]Graphics card: ATI Radeon HD 6970

CPU: AMD Phenom II X6 1090T

PSU: Thermaltake TR2-800AH2NFB

RAM: I'm not sure what kind of RAM I've got, however I do know that I have 4GB of it and I ran a memtest on it. It showed no problems with it at all.

Motherboard: ASUS M4A89GTD Pro

[/B]Again, I apologize for the extremely stupid question but I'm really desperate here. I'm loving Ubuntu on my laptop and I think I would love it even more on a fairly decent gaming PC instead of having to use Windows 7 to do things Ubuntu can do even better.

---

### Post by Q-ro on 2012-10-20
I think that it could be something with your hard drive, so i'm going to ask you some thing:

¿is your system only running ubuntu, or is the disk partition?
¿have you tried any hard drive tool for bad sectors?

I'm going to assume that the answer to #2 is not, in that case i recommend you download hiren's boot and do a HD check with either DRevitalize 1.2, or 
Western Digital Data Lifeguard Tools 1.24 if you happen to have a western digital HD.

Let me know if it worked, or if you need help with any of the steps :D (also answer the questions :P).

---

### Post by hexg on 2012-10-20
> **Q-ro said:**
> I think that it could be something with your hard drive, so i'm going to ask you some thing:

¿is your system only running ubuntu, or is the disk partition?
¿have you tried any hard drive tool for bad sectors?

I'm going to assume that the answer to #2 is not, in that case i recommend you download hiren's boot and do a HD check with either DRevitalize 1.2, or 
Western Digital Data Lifeguard Tools 1.24 if you happen to have a western digital HD.

Let me know if it worked, or if you need help with any of the steps :D (also answer the questions :P).

The disk is partitioned, I have two hard drives. My first hard drive is partitioned into two partitions. One for Windows 7 64 bit and one for Windows 7 32 bit. My second hard drive is just for big files that I don't  want clogging up my machine. I'll try a hard drive checking tool now. Thanks for the answer.

Edit: Oh, and yes both of the hard drives are made by Western Digital.

---

### Post by 2F4U on 2012-10-20
Did you run a memory test recently? On random freezes a possible reason may be a corrupt RAM chip. If you decide to run memtest, let it run for several rounds, since memory problems often don't show up during the first cycle (happend to me).

---

### Post by hexg on 2012-10-20
> **2F4U said:**
> Did you run a memory test recently? On random freezes a possible reason may be a corrupt RAM chip. If you decide to run memtest, let it run for several rounds, since memory problems often don't show up during the first cycle (happend to me).

I ran it overnight and it found nothing.

---

### Post by hexg on 2012-10-20
So after running the Western Digital Data Lifeguard Tools it said some sectors are bad and can be repaired. When I hit "repair" it said I should back up my data on the drive I'm attempting to repair, but I had already backed up all my important things a while ago when trying to install Ubuntu for the first time.

When I started the bad sector repair I got this message:
[IMG]http://i.imgur.com/EMCBB.png[/IMG]
If you can't see the image the error message says:
Error was detected while repairing bad sectors. Please contact WD technical support for help.
Should I try another disk tool or should I just give up?

---

### Post by Q-ro on 2012-10-20
That's odd :/, ¿ how about DRevitalize 1.2 ?¿ does it show the same error ?

Since you have windows 7 installed, ¿ have you try using the windows tool for scaning and repairing disks ? (i think all you have to do is go to system, then right click the HD and go to options, and there you can find the scan for bad sectors [or something like that], it also repairs bad sector if any ).

---

### Post by hexg on 2012-10-20
> **Q-ro said:**
> That's odd :/, ¿ how about DRevitalize 1.2 ?¿ does it show the same error ?

Since you have windows 7 installed, ¿ have you try using the windows tool for scaning and repairing disks ? (i think all you have to do is go to system, then right click the HD and go to options, and there you can find the scan for bad sectors [or something like that], it also repairs bad sector if any ).

I'll try DRevitalize now. If it shows that error I'll try the official Windows 7 tool.

---

### Post by hexg on 2012-10-21
Well after doing some more testing it seems that the issue isn't my ram, or my hard drive. It's my graphics card. I just noticed that when I started Ubuntu the fan speed would quickly go faster and faster, and in some games on Windows it did that exact thing when my PC was about to crash, and the crashes were exactly the same as they are in Ubuntu, no key combination to kill a process or to open the task manager worked and I had to reset my computer by holding the power button.

Sorry for being such a bother, that should have been the first thing I considered when trying to fix it. I guess I'll just have to bear with Windows until I can get an Nvidia card, I swear I've had nothing but problems with ATI.

Anyways thanks to the people that took their time to try and help me, even though it didn't fix my issue I got lots of handy tools to use in case I mess up my install of Windows. I'll mark the thread as solved to save the mods time, and hopefully I'll see you all later once I get a new card. I also apologize for the double post but when I try to edit my post the page just doesn't load for some reason.

---

