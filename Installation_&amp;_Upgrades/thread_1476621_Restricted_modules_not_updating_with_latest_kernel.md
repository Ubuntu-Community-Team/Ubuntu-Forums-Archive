---
title: "Restricted modules not updating with latest kernel updates, Lucid 10.04"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by ewz on 2010-05-08
Hi all, 
I have noticed in the recent updates there is a Kernel update 2.6.32-22
but there is no restricted modules included.
On my Desktop I have a Nvidia card which I installed the driver using the **Hardware Drivers Application**.  As far as I know these Drivers are ether reinstalled or updated whenever there is a kernel update.

I also have a Laptop with a ATI Radeon card which I did run the updates and ended up (after the reboot) in low graphics mode, after a bit of work I was able to reinstall the drivers and get my desktop back so that's ok now.

I had this problem a few years ago with an old version of Ubuntu, kernel updates but no restricted drivers. The drivers turned up the next day and all was fine.
I was just wandering if this is a known issue with Lucid or if anyone else has had this problem, 
It's been a couple of days since I noticed the Kernel update but still Restricted Modules.
Oh I'm using Ubuntu Lucid 10.04

Thanks for the help :)

---

### Post by djchandler on 2010-05-08
I don't believe this is a problem.

I have experienced as many as three kernel updates while beta testing, and easily at least two within a single regular release without getting a new fglrx (ATI Radeon) driver. The only time it's really necessary is with a version upgrade, and that's not necessarily a different driver, just a different .deb build for compatibility with a new kernel.

I doubt there will be any major updates (bug fixes only) until we see the 2.6.33-x kernel with the release of 10.10 (Maverick) in October.

---

### Post by Kulgan on 2010-05-12
After a fresh install of Lucid, restricted drivers no longer appear in "Hardware Drivers" (jockey). Although they did appear when I was running the LiveCD. 

Additionally, the time server appears to be two hours off (CEST).

Edit:
I spoke too quickly. After updates and reboot, the restricted drivers (wireless, ATI) are available through Jockey.

---

