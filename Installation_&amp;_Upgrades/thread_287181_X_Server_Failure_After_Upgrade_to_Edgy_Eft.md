---
title: "X Server Failure After Upgrade to Edgy Eft"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by philliplemky on 2006-10-28
Hi,

I had Dapper Drake installed on a PC with a Riva TNT2 video card.  I was using the nvidia-glx-legacy driver for that card.

I just upgraded to Edgy Eft and it looks like some changes were made to Nvidia drivers.  (I only found this out after the fact.  I should have checked that out before upgrading.)  Anyway, now, when booting Edgy, I get the following:

-----
Error: API mismatch: the NVIDIA kernel module is version 1.0.7184, but this X module is version 1.0.7174.  Please be sure that your kernel module and all NVIDIA driver files have the same driver version.

(EE) NVIDIA (0): Failed to initialize the NVIDIA kernel module!
(EE) NVIDIA (0): *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error: no screens found
-----

I'm still somewhat of a Linux newbie, so I'm not sure where to go from here.  Any help would be much appreciated.

---

### Post by DaveBorealis on 2006-10-28
> **philliplemky said:**
> 
I just upgraded to Edgy Eft and it looks like some changes were made to Nvidia drivers.

If no one comes through with a simple solution, you might want to consider reinstalling Dapper 6.06, or if possible, downgrading back to 6.06.  I've been noticing in the forum that Edgy isn't 100% compatible with all hardware, so for myself I'm going to try out the Edgy live CD, and if I encounter any problems I'll just wait a month or so and try it again.  When I get a clean live CD run on my system, then I'll upgrade!

Best regards,
Dave

---

### Post by philliplemky on 2006-10-28
Hi Dave,

Thanks for the advice.  It looks like that's the way to go (i.e. reinstalling Dapper).  I've been reading some of the other threads in this forum and a lot of other people are having install/upgrade issues with Edgy too.  Using a Live CD before installing/upgrading is a good idea.  I wished I thought of that before upgrading.

***[SIZE=4]Phil[/SIZE]***

---

### Post by LuisC-SM on 2006-10-28
> **DaveBorealis said:**
> ..., so for myself I'm going to try out the Edgy live CD, and if I encounter any problems I'll just wait a month or so and try it again.  When I get a clean live CD run on my system, then I'll upgrade!

Best regards,
Dave

Well, I used the liveCD and found no single problem, my RADEON card was just working very nice... problems will start after upgrading, so just be carefull

Regards.

Luis C. Suárez

---

