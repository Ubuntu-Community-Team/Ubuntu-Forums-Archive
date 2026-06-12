---
title: "Would like to install Ubuntu with software based RAID 1"
date: 2016-04-11
forum: Installation &amp; Upgrades
---

### Post by chris-hancox on 2016-04-11
Hi everyone.

I have a system with two 4TB drives and the board does not support RAID. I'd like to install Ubuntu 16.04 LTS onto one drive and add the other in RAID 1 so I have redundancy.

I have no idea how to do this but it is apparently possible. A lot of articles seem to reference old versions of Ubuntu and the new installer lacks these options.

I am grateful for any assistance. :)

---

### Post by bcschmerker on 2016-04-12
**Looks as though your problem is rather similar to mine.**  I'm currently pondering adding a fourth Toshiba® PH2050U-1I54 to the three already in my own rig and reformatting as two RAID 1 pairs (of two 500GiB HDD's each), using the carryover Seagate® ST382015A (from the prior Ubuntu® 12.04.6-LTS install), or alternately the also-recently-added Western Digital® WD1600JS-55NCB1, for /boot, swap and filesystem root under Ubuntu® 16.04.0-LTS.  (I haven't attempted to use hardware RAID to date on my Gigabyte® GA-MA78GM-S2HP Rev. 2.0; it does support RAID on the SATA subsystem according to the factory documentation.)

---

### Post by chris-hancox on 2016-04-12
I'd like to use the two 4TB drives as boot drives if all all possible.

I know that some Gigabyte boards use 3rd party controllers which have performance issues so make sure you think about that also.

---

### Post by JP_Rockagetty_III on 2016-04-22
I would also like to install RAID-1 for a file server.  A couple of years ago, I got Ubuntu Desktop and Samba working on an old system, and created a shared directory - having network storage, instantly accessible, was better than burning backup data to DVDs, and WAY better than using Travan tape cartridges!  Right now, I have kodibuntu working on one of my machines, and NAS4FREE (which is BSD-based) on another machine. So I think I have the skills to make Ubuntu RAID-1 work, if I can find a more recent tutorial.

It would be nice to install both Samba and KODI on this server, so I could have a combination video and file server.  Yes, RAID-1 is not an efficient use of space for video entertainment - I could always rip the DVDs again if a drive fails.  But for my financial records, I want redundancy, and a RAID system that I can understand - and that is RAID-1.

There are a couple of tutorials out there that suggest using "Ubuntu SERVER" and the "Guided" RAID install that it has.  Then install Ubuntu-desktop afterwards.  I have not tried this, but I might try it soon.

---

### Post by JP_Rockagetty_III on 2016-04-28
Let me just put this here:

[http://linux-sys-adm.com/how-to-install-and-activate-raid-1-ubuntu-server-14.04-lts-step-by-step-by-step/](http://linux-sys-adm.com/how-to-install-and-activate-raid-1-ubuntu-server-14.04-lts-step-by-step-by-step/)

I have not tried this; I do not know if this works or not.  But I did get RAID-1 to work (with identical ZFS-formatted 320 GB SATA drives) under NAS4FREE.  I'll follow the link above in a few weeks.  When I get all the parts, I will try to set up Ubuntu Server according to those directions.  Then I'll install KODI, because it plays VOB files, and I don't have to touch physical DVDs to enjoy my entertainment (and KODI is cool as well).

I will try really hard to get RAID-1 to work under Ubuntu.  If I succeed, I'll try to remember to post in this thread how it was done.[URL="http://linux-sys-adm.com/how-to-install-and-activate-raid-1-ubuntu-server-14.04-lts-step-by-step-by-step/"]
[/URL]

---

### Post by JP_Rockagetty_III on 2016-05-24
Okay, I've got the parts now:  Asrock AM1H-ITX, AMD 5350, 8 GB Ram Arctic Alpine M1-Passive CPU cooler Two 3 TB HGST drives Fractal Design Node 304 case Seasonic 600W PSU  Here are the guides I am using:  [https://help.ubuntu.com/lts/serverguide/advanced-installation.html](https://help.ubuntu.com/lts/serverguide/advanced-installation.html) [http://linux-sys-adm.com/how-to-install-and-activate-raid-1-ubuntu-server-14.04-lts-step-by-step-by-step/](http://linux-sys-adm.com/how-to-install-and-activate-raid-1-ubuntu-server-14.04-lts-step-by-step-by-step/)  A few questions:  1.  If I remove the DVD-RW after the initial setup, will this cause a problem?  My case doesn't have an exposed 5.25-inch bay.  2.  Will I really set up both disks with identical partitions?  Will root and swap (and /lib, /var, whatever) be duplicated on both disks?  3.  If the disk with GRUB on it fails, and I boot the other disk from a rescue DVD, can I insert a fresh hard drive and get it to rebuild, as if the failure never happened?  4.  If I get a rescue disk that knows about GPT partitions, would something like gparted know the disks are in a RAID array?  Would the partition table be something human-readable, so I know I succeeded?  The pre-built units (Synology, etc.) really did look good, but I thought I could do better building it myself.  Does anyone have experience doing RAID-1 on 16.04 yet?  Is there anything I should watch out for?  Any help is greatly appreciated.

---

