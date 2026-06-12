---
title: "How to install new motherboard driver?"
date: 2012-03-29
forum: Installation &amp; Upgrades
---

### Post by hodad on 2012-03-29
I have a Biostar MCP6PB M2 + N68S motherboard.   It seems to be pretty flaky (it was cheap). I'm running an AMD quad core processor on it.

Does anyone know the procedure for installing a new motherboard driver without using the Windows-based CD they included with the MOBO?

Also, does it matter that the driver was produced for Windows, or should I look for one tailored towards Linux? (Don't think there is one, though).

Thanks

---

### Post by QIII on 2012-03-29
Everything on that driver disk will be Windows drivers and probably none of the installation apps will work in Linux.  The OEM may have Linux drivers, but I doubt it.  Certainly not a comprehensive CD.  Most everything should work fine.  For the things that don't we are red-headed step children.

But we can help you find solutions.

What is flakey?

---

### Post by hodad on 2012-03-29
I've had trouble since I cobbled together this box from parts of my previous PC: Tower case, 380W ps, AMD quad core (Phenom?, can't remember exactly), 480MB HD.  Bought the Biostar mainly because it was a match for the AMD processor (previous mobo died a static induced death).

Installed 11.10, and it worked fine, but I could never get upgrade manager to work. Never could figure out why, though I made many attempts, following advice on this forum.   System operation got increasingly flaky (screen got the jitters, freezups, etc).  Kept trying to update via GUI update mgr, and terminal apt-get, but nothing worked, until I tried again yesterday, and the pc flat died. 

After mucking around changing drives, etc, I suspect the MOBO.  Have tried to install a known good AMD64 DVD version of 11.10 several times today, but it has failed each time.  Goes about 95% through the process, and it dies, either with or without an error message.  Sometimes the screen goes haywire, and I have to kill the power to get out of it.     Tried install w updates and w/o updates.  No luck.  I even hooked the HD up inside my other linux box and formatted it, and tried installing again. Again, no joy. I suspect the MOBO, even though it's only a few months old, and I installed it carefully.  If I had any money, I'd throw it out and get a new one, but...

---

### Post by Bucky Ball on 2012-03-29
If it's only a few months old it should still be under warranty.

Are you talking about flashing the BIOS when you say 'motherboard drivers'?

---

### Post by QIII on 2012-03-29
I wouldn't count that mobo out of the action just yet, anyway.  A static discharge on the board could have damaged any number of things:  cpu, memory, anything in pci slots, pcbs in the drives, drive firmware.  It's entirely possible for a mobo to pass POST with a whole lot of things wrong.

It could also be as simple as setting nomodset on startup.

---

### Post by QIII on 2012-03-29
If you had an old AM2+ Phenom and put it in one of the boards that will handle AM2/AM2+/AM3 processors, it could be a matter of whether dual channel is supported for your memory and you might need to rearrange the modules in the slots.

---

### Post by hodad on 2012-04-09
Sorry for the delay in answering...

By the process of elimination, I determined that it was the mobo, and replaced it with an ASRock A770DE+.  It started up right away with same components installed, no problem.  

I appreciate your ideas, however.  Back up and running with 12.04 Beta, Seems to be running smooth.

Thanks!

---

### Post by Bucky Ball on 2012-04-09
Excellent. Please mark thread as 'Solved' from Thread Tools. ;)

---

