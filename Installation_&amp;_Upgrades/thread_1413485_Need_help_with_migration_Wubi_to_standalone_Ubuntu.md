---
title: "Need help with migration: Wubi to standalone Ubuntu 9.10"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by Chromagnum on 2010-02-22
I need some help with migration from Wubi to standalone Ubuntu 9.10. I already read some guides about migration but didn't quite understand, or perhaps I'm to scared to try. 

These are information about my spesification:

-P4 dual core 3Ghz, 1 GB DDR, and Nvidia FX5500 (I know this is probably not important, but who knows...)

-2 Physical Hdd's: 10 GB Quantum Fireball IDE and 160 GB Hitachi Sata.

10 GB Quantum (NTFS) contains Windows XP SP2 only, nothing else. 160 GB contains 3 partitions; 20 GB, 50GB and 80GB (all NTFS). When I installed Ubuntu 9.10 via Wubi, I used 20 GB partition, which is now contains Ubuntu installation. 50 and 80 GB contained only data, which was already being backuped to another external Hdd. So in short: both of them are free now.

I'm planning to get rid of 10 GB Quantum from my system, to use as an external Hdd, so I don't really care about Windows XP anymore. I only need 160 GB Hitachi. Right now all the filesystem in 20 GB partition. 50 and 80 are empties. I would like to just join them all so it would be 160 GB again. 

So, can anyone guide me through this migration procedure so I don't need a fresh installation? I'm quite happy with everything I've done with my Karmic; everything I need already there. I just need to get rid of Wubi (and *cough* windows). 

Thank you in advance.

---

### Post by ubunterooster on 2010-02-22
Hi Cromagnum! Actually what you are attempting is a bit difficult. My reccomendation is to copy the entire home folder to an external drive or other media and then to go through a reinstall.
  In my travells, I have at times just written down all relevant info (programs, settings...passwords), copied my entire home folder, and reinstalled, just to get rid of any unneeded programs b/c it was no big deal.  
  When pasting folders from old home to new, I merge folders and replace files. [then I remove gnome-games, evolution...everything I don't use]

---

### Post by Chromagnum on 2010-02-23
> **ubunterooster said:**
> Hi Cromagnum! Actually what you are attempting is a bit difficult. My reccomendation is to copy the entire home folder to an external drive or other media and then to go through a reinstall.
  In my travells, I have at times just written down all relevant info (programs, settings...passwords), copied my entire home folder, and reinstalled, just to get rid of any unneeded programs b/c it was no big deal.  
  When pasting folders from old home to new, I merge folders and replace files. [then I remove gnome-games, evolution...everything I don't use]

Thank you for your reply, but after whole day thinking about it (and constant screaming in my head mainly because of my friend gave me loads of horror stories about Wubi migration to standalone installation), I finally performed a clean installation. So I guess I don't need help with Wubi anymore.

Perhaps someday there is a method build in Wubi to perform that on the fly; yeah, someday. Not really important, though. But Wubi sure does help me with Ubuntu when I first started, gotta gives credit for that. Anyway, I'm gonna close this thread since I'm already on clean Karmic installation. Thanks again ubunterooster, really appreciated.

---

