---
title: "It's great that Ubuntu has so many security updates, but..."
date: 2012-07-06
forum: Installation &amp; Upgrades
---

### Post by BcRich on 2012-07-06
I'm using Ubuntu and Kubuntu 12.04 and luvin it! and also really like that there are regular security fixes available through update manager.
I'm also using the proprietary AMD Catalyst drivers.
The problem I'm having is that since I've upgraded to 12.04 there have been numerous updates to the x window system and the kernel. Not that I'm complaining about the updates (cause I think it's great that bugs are fixed so rapidly, even though I haven't  experienced any major ones as of yet). The actual problem is that each time one of these components is updated X fails to start. I realize this has to do with the Catalyst driver, as I am booted into a CLI at which point I have to reinstall the AMD driver. Reboot and everything is fine. I then have to re-configure my Catalyst drivers (once in Ubuntu) to the previous setup (because I have two monitors running off two GPU's), This in turn requires two additional restarts. That's a total of 3 restarts, in case you weren't counting :)  
Anyway, am I seriously the only person having this problem? Surely there must be alot of Ubuntu users out there running Catalyst on 12.04 experiencing this issue, or not?
Do you have any suggestions for me as to how I can avoid this issue, keep the Catalyst drivers and still obtain the security fixes (incl X and kernel updates)?
I suppose it wouldn't be such a big issue if the the kernel and X window system were updated at the same time. In other words not have an X update causing the graphics driver re-installation issue, then having a kernel update a few days later causing the same issue again. I imagine that all updates identified by Update Manager are from an official Ubuntu/ Canonical team? If so why are the updates not delivered in a more system-contextualized time-frame? Or perhaps they are?
This is not a complaint btw, I'm just curious and looking for a way of avoiding this problem I've been having.
I hope that people that are new to Ubuntu and using similar setups are not put off by this problem as expecting to boot up your computer as normal and being kicked to a CLI (I'd imagine) could be quite a challenge for a new comer.
Thanks if you can offer and comments or help :)

---

### Post by QIII on 2012-07-06
How have you been installing the driver?

---

### Post by BcRich on 2012-07-06
> **QIII said:**
> How have you been installing the driver?
Hi QIII
it's an .sh file, just by simply running the file with sudo

---

### Post by QIII on 2012-07-07
From the AMD website?

If you install it from the Ubuntu repo, it will be compiled into the new kernel on update.

---

### Post by BcRich on 2012-07-07
sorry my bad it's a .run file not .sh and yes, It's from the AMD website.
thanks for the heads-up, I did not know that Ubuntu repos stored proprietary software too. Or did the drivers go open source ( I seem to remember AMD saying they were heading in that direction years ago)? 
Is the name of the package you are referring to "fglrx-amdcccle"?
thanks for the help QIII :)

---

### Post by Bucky Ball on 2012-07-07
They don't. The AMD catalyst drivers are third party and NOT in the repos (open source fglrx drivers are but 2D).

---

### Post by m420n on 2012-07-08
I have the same problem (and more) with the AMD driver from the repos. Today my desktop (FireGL v3700) didnt boot at all. First it showed only a black screen and the monitor went off. Then I had various segmentation faults or other kernel errors. This seems to be caused by the updates I installed yesterday. Also the AMD driver causes other problems on my notebook.

---

### Post by QIII on 2012-07-08
> **Bucky Ball said:**
> They don't. The AMD catalyst drivers are third party and NOT in the repos (open source fglrx drivers are but 2D).

This is a case where a proprietary driver is in the repo.

---

### Post by QIII on 2012-07-08
> **m420n said:**
> I have the same problem (and more) with the AMD driver from the repos. Today my desktop (FireGL v3700) didnt boot at all. First it showed only a black screen and the monitor went off. Then I had various segmentation faults or other kernel errors. This seems to be caused by the updates I installed yesterday. Also the AMD driver causes other problems on my notebook.

The card in your desktop is no longer supported by the current fglrx driver.  The legacy driver for it will not work with the current X server.  You will need to use the default open source Radeon driver.

Can you give me the specs on your laptop?  If it has hybrid Intel/AMD grahics, your difficulty is not uncommon.

---

### Post by BcRich on 2012-07-12
Yay another x-server update today :/
graphics driver re-installation and 3 restarts later....
@QIII not to sound sceptical  or anything like that but do you perhaps know of a source that I can verify that the driver in the repos is indeed the one I'm looking for (i.e. AMD Catalyst driver)?
I'm considering changing my driver if it means being able to avoid these driver issues.
Thanks :)

---

