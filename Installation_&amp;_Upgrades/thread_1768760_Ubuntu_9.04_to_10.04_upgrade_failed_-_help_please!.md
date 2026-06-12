---
title: "Ubuntu 9.04 to 10.04 upgrade failed - help please!"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by Giradman on 2011-05-27
Hello all - been a while since I've been here but seems active as ever! :)

Last night I attempted to upgrade my old IBM laptop from 9.04 (support just expired) to 10.4 LTS - seemed to be doing fine until a bug report dialog box appeared stating a desktop application bug; I saved the file to the DT and was planning to view later.

However, on multiple attempts to reboot the computer, the program gets to the opening Ubuntu logo, then the screen goes black, & and hard drive symbol is unlit - just frozen.  Is there anyway to recover from this problem or do I need to start anew?  the machine has no internal CD drive (have an external one from which I loaded my original Ubuntu distro probably 3 yrs ago or so).  I do have a large USB thumb drive but not sure if this laptop would boot a live distro from it?

Any suggestions or help would be appreciated - thanks, as always.  :(

---

### Post by mörgæs on 2011-05-27
I would try a live boot of 10.04 or 10.10 and after that a fresh install, if it works. You might end with spending much more time doing the upgrade than the new install.

---

### Post by Giradman on 2011-05-27
Thanks **mörgæs** for your comments - unfortunately, I am kind of stuck w/ the suggestion; my computer is an old IBM ThinkPad X40 - I can get to the BIOS menu but there is no option to boot from my external CD drive.

I can also get into a terminal window, and I assume that I would need to 'wipe' the hard drive, and then reboot w/ a CD containing the 10.04 LTS iso (which I made today); however, I am not sure how to exactly 'wipe' this HD and prepare it for the iso boot?

Any more help would be appreciated - thanks. :confused:

---

### Post by e79 on 2011-05-27
At this point here is I would do :

1. As mörgæs suggested, try to boot from a live CD (either internal or external, one of them must work as there is an operating system installed!)

2. When you can boot from it, select the option to 'Try Ubuntu', this will hopefully lead you to a fresh desktop from the live CD.

3. Plug in an external USB thumb/drive and backup everything you need (home folder etc.)

4. Download Ultimate Boot CD from [http://www.ultimatebootcd.com/download.html](http://www.ultimatebootcd.com/download.html), burn it to a cd and boot your machine with it.

5.To wipe your hard drive,  select the category 'HDD' and select DBAN (Darick's Boot and Nuke) and check at the option to select the erase method called 'One pass (all zeros)'; and wipe your hard drive. If that does not work, you can also try (I think its called) HDD Erase from the same CD using the same 'one pass(zeroed)' option. They would effectively wipe your hard drive by rewriting zeros all over it.

6. Once done, do a fresh install of your version of your choice (10.04/10.10/11.04) and and copy back (restore) all your data backed up in step 3  :p

Hope this helps

---

### Post by Hedgehog1 on 2011-05-28
> **Giradman said:**
> **my computer is an old IBM ThinkPad X40 - I can get to the BIOS menu but there is no option to boot from my external CD drive.**

If you cannot boot from a CD, and the laptop will not boot from USB, your options are very limited.

Some forum members have removed the hard drive from a laptop like this, and installed Ubuntu on it using a different PC, and then reinstalled the hard drive into the laptop.

Just a thought.

***The Hedge***

:KS

---

### Post by mörgæs on 2011-05-28
Plop boot manager might be worth trying

[http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

---

### Post by Giradman on 2011-05-28
> **Hedgehog1 said:**
> If you cannot boot from a CD, and the laptop will not boot from USB, your options are very limited.

Some forum members have removed the hard drive from a laptop like this, and installed Ubuntu on it using a different PC, and then reinstalled the hard drive into the laptop.

Thanks **Hedge & Others** - well, using another way in I was able to get to the boot order and could select an external CD or USB boot - needed to disable the internal drive.

I tried 2 different iso images & one iso on a USB thumb drive, but kept getting the message below:

PXE-E61 - Media test failure, check cable
PXE-MOF - Existing Intel boot agent
Operating system not found

Assume the OS is not found because of the PXE-E61 issue - don't really understand the problem but will 'google' it!  Thanks again - :(

---

### Post by Giradman on 2011-05-29
Well, I've marked this thread as 'Solved' but not really - despite trying I just could not resolve the issues discussed to get an Ubuntu upgrade on this old IBM laptop.

In another computer forum (Cybertechhelp), I had left a similar thread and one poster had the same problems and frustrations as I did in this thread - he switched to PCLinuxOS; well I downloaded the iso & installer, booted from the external CD drive, and was able to load the program onto my laptop - will play around w/ this other version for a while (use the GNOME GUI interface version).

Thanks again for all of the suggestions - :)

---

### Post by mörgæs on 2011-05-29
> **Giradman said:**
> 

PXE-E61 - Media test failure, check cable
PXE-MOF - Existing Intel boot agent
Operating system not found

Assume the OS is not found because of the PXE-E61 issue - don't really understand the problem but will 'google' it!  Thanks again - :(


This is an easy problem to solve. PXE means booting over network (unlike the normal boot using local storage, like a hard drive or CD). 

Just change the boot settings in BIOS.

---

