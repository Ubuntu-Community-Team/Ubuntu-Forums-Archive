---
title: "Fresh 15.1 server install - stuck at grub&gt;"
date: 2016-01-02
forum: Installation &amp; Upgrades
---

### Post by intipsicated on 2016-01-02
Please forgive me if this has been answered.
Also, there will be some extra data given to ensure I'm getting it all communicated. Better too much than too little.

Backstory - I ran my ts440 for about a year with Ubuntu 12.something (desktop version) installed on a couple of 120g ssds running raid 1 (why not raid 0? Because n00b mistakes and fear of dataloss, that's why)

This ran as my main desktop/plex server with very few minor hitches. (Home was too small, root was too big, some transcoding lags)

This server also houses my hw raid, WHICH ALWAYS MOUNTS AS HD0 (perhaps important data)

This week I decided to go for the gold and use the server as a dedicated server. I started by booting to a full install of 12desktop I have on a flashdrive and wiping the drives completely. 
I then booted to an Ubuntu 15.1 install flashdrive and used lvm guided on one of the ssds, figuring I can extent to the other drive later.

CURRENT ISSUE

The install claimed success and rebooted. (Yes I pulled the flashdrive)
It boots to grub 2.02

grub>

ls shows the logical swap and root volumes, the raid, both physical ssds including the physical volumes on the drive I installed to and a 4th drive that doesn't exist labeled (hd3)

(Hd3) gets 
error: failure reading sector 0xfc
Error: failure reading sector 0xe0
Error: failure reading sector 0x0

ls (lvm/[mylogicalroot])/ shows Linux did install...

What next?
Teach me the ways of the force, or grub at the very least.

---

