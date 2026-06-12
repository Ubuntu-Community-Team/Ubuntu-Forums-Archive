---
title: "&quot;Unable to boot from hard disk&quot; after install"
date: 2006-11-27
forum: Installation &amp; Upgrades
---

### Post by djrobthaman on 2006-11-27
Hi,

I've been trying to install edgy on my pc (see specs below) to no avail.  I get the live cd to boot up and it seems to run fine and the install looks to work properly but when I restart after the install and choose to boot ubuntu I get a message that says something like "Unable to boot from disk" (I can't remember the exact wording, I have since installed Suse 10.1 but would really want to install ubuntu).

I downloaded the amd 86x64 desktop cd because my system is 64 bit.  Is there anything I can do to successfully install Ubuntu?

Thanks a lot,
Douglas


Specs:

MB: Foxconn 925XE7AA-8EKRS2 925XE 775
CPU: Intel Pentium 4 541 Prescott 3.2 GHz LGA 775
RAM: G. Skill Extreme Series 1GB 240-pin DDR2 533 (PC4200)
Video: ATI 100-714600 Radeon X1300 256MB DDR PCI Express x16 All-In-Wonder 2006 Edition
HD:
Seagate Barracuda ST3320620A 7200 RPM IDE Ultra ATA100 320GB (x2)
Western Digital Caviar SE WD2000JB 7200 RPM Ultra ATA100 200GB
Another 180GB drive I salvaged from my brother's Dell

---

### Post by djrobthaman on 2006-11-27
Hi,

I hate when people do this too (reply to their own posts just to get it higher up in the forum), but does anyone have any thoughts or know of anywhere that might find any information on how to fix my problem.

THanks again,
Douglas

---

### Post by howipepper on 2007-01-10
I had a similar problem trying to reinstall 6.10 to my Dell.  I had originally installed 6.10 with no problems, but after messing around in it, thought I might want it fresh.  This time, no matter what I did, it would not boot after the install completed.  I darned near pulled out the rest of my hair!  Finally, I used Lilo instead of Grub, and it worked again.

I had tried both the regular and the alternate CD, as well as the alternate x86-64 CD (my Dell has a dual-core Pentium D processor in it).  On all of them, I used the "Expert" mode for my install.  I still haven't found out why it wouldn't boot, but using Lilo saved the day.

---

### Post by Silver_Seagull on 2007-01-10
I had the same issue as you djrob- I found GRUB automatically installs itself to the first/master IDE HDD on the first IDE channel.  I changed my HDD boot order to my "storage drive" first, and no issues since :)

---

### Post by sandysandy on 2007-10-07
i am unable to boot from HDD after installing ubuntu 7.04, though i am able to boot from live CD . when i try the option boot from first disk (when booting from live CD), disk failure message comes. But when i see the HDD the ubuntu files are there. Kindly help. trying to convert to Linux.

---

