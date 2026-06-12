---
title: "optimum partition sizes"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by smCw6GNakQn300£ on 2010-03-30
Hi folks,

I'm going to be upgrading to Lucid soon, and rather than upgrade, I will be doing a fresh install.

I know to keep a note of my installed programs, and sources list, but I also want to create a separate partition for "/home".

Does anyone know the best size of partition to reserve for root and swap?
That way, I'll know how much to leave for /home


Also, to copy all of my program settings etc, is it as easy as taking a copy of my current /home directory before re-installing, and then restoring this copy after installation?

Cheers.

---

### Post by ajgreeny on 2010-03-30
> **BRY said:**
> Hi folks,

I'm going to be upgrading to Lucid soon, and rather than upgrade, I will be doing a fresh install.

I know to keep a not of my installed programs, and sources list, but I also want to create a separate partition for "/home".

Does anyone know the best size of partition to reserve for root and swap?
That way, I'll know how much to leave for /home


Also, to copy all of my program settings etc, is it as easy as taking a copy of my current /home directory before re-installing, and then restoring this copy after installation?

Cheers.
Good idea to do a clean install, or I think so at any rate.  I've never upgraded so far in the 5 years of using ubuntu, and it's so easy to backup and reinstall that I think you are doing the right thing.

As for partition sizes, that is a question of how much you intend to add to your system and how many personal files, videos, music, etc etc you keep in your home partition as opposed to elsewhere, perhaps a NAS system.

I have a root partition of 10GB, and have added quite a lot of extras to the standard default ubuntu, but my root partition is only using 3.6GB, so plenty of headroom there, however, 10GB seems to be the generally accepted size you will see written about in very many places.  My /home partition takes the rest of the 160GB disk, apart from a swap of 2GB, ie 148GB.

Swap size suggested, used to be twice the size of your ram, but with modern systems having GBs of ram, that is often not needed.  My system with 2GB ram and 2GB swap is plenty for me, and swap is seldom if ever used, though I admit I never suspend or hibernate as the hardware will not do that properly for me, and never comes back out properly.

Regarding what to back up and restore, I think you are basically correct; everything in your current home, including all the hidden folders and files is probably all you need.  Some people would probably suggest keeping /etc as well, but personally I think that is overkill, and not worth doing.  You pay your money and take your choice on that one.

Wait and see what others say, but even if you went ahead like that now, it would be very quick to get the new install back to what you want.

---

