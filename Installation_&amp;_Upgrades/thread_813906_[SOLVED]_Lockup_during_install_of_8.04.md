---
title: "[SOLVED] Lockup during install of 8.04"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by Rustafur on 2008-05-31
I'm having a real head-banging-against-the-wall moment here guys.

I'm trying to install 8.04 on an AMD box (Sempron 3300+, Gigabyte nForce 350, 1GB RAM, Linksys WiFi card, GeForce 6800GT) and it's failing miserably to the tune of a hard crash during installation. What happens is I boot to CD, select Install Ubunutu, and it loads the Linux Kernel. After that, when Ubuntu goes to load the splash screen, the computer crashes hard -no response from keyboard, mouse or anything.

I've tried both the 32 bit and AMD64 flavors of Ubuntu and even linux mint. With Mint I was at least able to get the Live CD to boot up and begin the installation process to the point where it starts the partition manager before it too would crash. But usually it too would crash soon after loading the Kernel and trying to boot up the splash screen and load the Live CD desktop environment. 

I'm at a loss here guys, and I think my wife's starting to loose patience with me (it's her computer). Any help would be great, thanks in advance!

---

### Post by ugm6hr on 2008-05-31
Did you check the CD for errors?

It is one of the options on booting.

Is the Sempron a 64-bit processor?  I didn't realise.

---

### Post by Rustafur on 2008-05-31
Thanks for the quick reply,

I didn't check the CD for errors during the install, I did check it for errors in Brasero on my machine though, and I've tried several discs and even different CD burners, so I think I've ruled out the production of the disc being the problem, unless the drive on the computer I'm installing to is having problems reading discs. I'll try doing a disc error check all the same though.

Yes, this processor was the of the first of the Sempron series to have the 64-bit instruction enabled. It's a Socket 754.

---

### Post by ugm6hr on 2008-05-31
> With Mint I was at least able to get the Live CD to boot up and begin the installation process to the point where it starts the partition manager before it too would crash. But usually it too would crash soon after loading the Kernel and trying to boot up the splash screen and load the Live CD desktop environment.
This suggests that the hardware can run Linux.

Also - have you installed any OS on it before?  Is it possible this is a hardware issue (e.g. RAM)?

> unless the drive on the computer I'm installing to is having problems reading discs.
Possible, but unusual.  Did you check md5 before burning?

---

### Post by Rustafur on 2008-05-31
> **ugm6hr said:**
> ...have you installed any OS on it before?  Is it possible this is a hardware issue (e.g. RAM)

Yes the box was running Windows XP before this Linux install attempt, and it has even run Linux in the past (Ubuntu 7.04 I believe). 

Also, I ran a disc check, no errors. After that I tried to install again (32 bit), and the process came to the point where I was running the Live CD, and had begun the install process, but it crashed during the HD formatting and partitioning. (Oh, I was so close I could taste it! lol) I shouldn't have to use the AMD64 version should I?

How do I run an MD5 check? (whoa! noob alert!)

---

### Post by ugm6hr on 2008-05-31
Hmmm. Bizarre.

Your hardware should be able to run the LiveCD and installer.  I have had problems with lower RAM computrers, but 1GB is plenty.

32- vs 64-bit is a long-running debate elsewhere in this forum.  Either should work.

Maybe try selecting the "Install directly" option from the boot menu.

If the CD checks out for errors, then I think md5 check is probably unnecessary (it checks the integrity of the original downloaded iso file).

Or perhaps the AlternateCD?

I'm a bit confused as to what is going on here.

---

### Post by Rustafur on 2008-05-31
> **ugm6hr said:**
> Hmmm. Bizarre.

Your hardware should be able to run the LiveCD and installer.  I have had problems with lower RAM computrers, but 1GB is plenty.

32- vs 64-bit is a long-running debate elsewhere in this forum.  Either should work.

Maybe try selecting the "Install directly" option from the boot menu.

If the CD checks out for errors, then I think md5 check is probably unnecessary (it checks the integrity of the original downloaded iso file).

Or perhaps the AlternateCD?

I'm a bit confused as to what is going on here.

You're not the only one confused here lol. I've tried to use the "Install Directly" option from the boot menu, but that's crashed as well. I'll give the AlternateCD a try and see what happens.

Also, the last 3 times I've tried to install, the process has crashed at the same point: The actual install starts up, the HD is formatted and the then partitioned, "Installing System, copying files" appears and then it crashes.

---

### Post by jobs2gates on 2008-05-31
Hey guys,
i ve been having the same problem. The kernel gets loaded and the system hangs while the splash screen has the horizontal bar oscillating.
i chcked the cd for errors but had none.
next, i ran the memory test and this gave me a number of memory errors. cud this be a reason for the installation failure ? What exactly does it mean when the memory test fails.

---

### Post by Rustafur on 2008-05-31
> **ugm6hr said:**
> Or perhaps the AlternateCD?

Bingo! The AlternateCD worked for installation!

And after a few rough boot-ups, the system is finally up and running. Thanks ugm6hr for the help and ideas!

---

### Post by Rustafur on 2008-06-14
I've seem to have solved my installation and rebooting problems. It turns out there was a hardware conflict, the RAM to be precise. 

After several tries at installing 8.04 I was finally able to get a successful installation by using the Alternate Install CD. However the core problem still seemed to be around as crashes would still randomly happen when the computer was rebooted. I just turned a blind eye to this, as it wasn't that big of a deal. THEN came the kernel update a few days ago, and that royally fouled up everything again. Booting to ANYTHING passed GRUB was just not happening. I tried running all of the fixes that you are able to perform during boot up, and they all did their job, but to no avail. I even tried running memtest86 for several hours, trying to single out a RAM error, but it too even passed with flying colors. So I assumed it must be a hardware problem, and I started with my RAM. I pulled one of the 512mb sticks out and I got lucky on the first try. For whatever reason my two sticks were conflicting with each other, even though they are the same memory, from the same manufacturer, and even passed several hours of memtest86.

I just wanted to let anyone who might read this thread in the future, that has a similar problem, of my solution. Don't give up! There's always a solution.

---

### Post by RESID3NT on 2008-06-14
I don't want to hijack this thread, but I have a similar problem on my rig.

I have a Q6600, 4GB ram, 8800gts and when I try to install the 64 bits of either 7.10 or 8.04 my computer just locks when I press either liveCD or installation.

Any hints/threads?

---

### Post by paddy1 on 2008-06-14
Just a wee word. I have tried to install Ubunto on Celeron and Athlon computers many times. 

My solution is to run the Maxtor disk diagnostic (runs on any harddrive), and run a complete low level format of the drive. This erases many items that might conflict with the installation, and has worked quite well for me.

Recycling and refurbishing older computers and donating to those in need

---

### Post by Rustafur on 2008-06-14
**RESID3NT** - Have you tried the Alternate Install CD, or the 32bit flavor of Ubuntu yet? 

**paddy1** - Maxtor's Maxblast software is some great formatting software, I swear by it myself.

---

