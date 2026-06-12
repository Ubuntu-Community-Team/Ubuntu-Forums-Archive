---
title: "Error: No root filesystem"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by chucklechops on 2006-06-01
Hello,
I'm trying to install Dapper on the first partition of my disk, which used to contain my old windows C drive. 

I have four other partitions on this drive, none of which I wish to lose: my old ubuntu installation, it's swap partition, an ntfs partition and a Fat32 partition.

In addition, I have 2 other drives: one PATA ntfs, and a SATA drive with my new windows installation, both of which I intend to keep.

During the installation I specify the first partition, my old windows c drive(51gb), as "/" and my old ubuntu swap partition(361mb) as "swap", requesting that both be formatted. When I click next I get the message "WARNING: This will destroy all data on any partitions you have removed as well as on the partitions that are going to be formatted.". 

I'm not sure what this means; it seems to suggest to me that ubuntu will format partitions for which I haven't set mount points. So I have carefully created mount points for all the partitions I wish to keep as well as my "/" and "swap" partitions. 

When I click 'install' I get the message "Error: no root filesystem", and since I clearly have specified a valid root filesystem I am at a loss... :confused: 

One of the things I tried was formatting my old c drive as ext3. This didn't resolve the problem but did destroy my MBR so now the only OS I can boot into is ubuntu installation CD, so I am a bit desperate.
TIA, Dave

---

### Post by therunnyman on 2006-06-01
Your problem is mine as well.  Dapper is loading the "card" SATA drives before the mobo drives, and has been for a great long while.  The devs acknowledge it, but don't do anything.

See if this helps: run a search on "Workaround therunnyman."  There some stuff there that may be of assistance.

Hope that helps.

therunnyman

---

### Post by chucklechops on 2006-06-02
Thanks for the reply; I tracked down your post and I'm pretty sure we have different problems; or I am too stupid to understand. Probably the latter. :) 

Anyway, since yesterday I managed to successfully install ubuntu on a different PATA drive. Unfortunately, grub failed to find my windows installation on the SATA drive. I messed around with various settings in Grub but couldn't get the sata drive to boot.

Needing to get into windows I went to the XP recovery console and did a fixmbr.

Now I can't boot windows, can't boot ubuntu.

There is no easy automated way to restore grub from the live CD that I can see. Tried the flight 7 installation CD 'restore grub' option: failed with an error message each time. The only OS I can get into is Dapper Live CD.

I have a valid installation of Windows and one of Ubuntu just sitting there and I am faced with a reinstallation of both.

I am pulling my hair out cos this should be SO STRAIGHTFORWARD. 

Any suggestions before I give up? 
TIA

---

