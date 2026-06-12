---
title: "Disk Error on /boot with dual boot on dual disk"
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by MartynT on 2010-12-30
Hi,

I have a (slightly complicated) dual/multi boot system.
I keep getting boot errors (when choosing ubuntu from the grub2 menu)
```
Serious errors were found while checking the disk drive for /boot
```
If I switch off and restart, ubuntu will then start without issue.

My setup is like this ....

3 disks,
one with 10.10 clean install - so Grub2, separate partitions for /, /boot and /home, 
one with windows 7,
one with windows XP and 10.04 wubi (this is my old disk which I will trash once I'm happy with my upgrade to 10.10 & 7 on separate disks.

I installed 7 and 10.10 with ONLY their disks installed.  After both were working, I added all disks and rejigged the grub2 menu (using update-grub and StartUp-Manager).

This problem only seems to occur if my previous boot was not 10.10 ( I will investigate this further).  It's as if something (grub2 ?, the bios ?) is remembering part of the previous boot and not using the grub2 menu completely.

Any suggestions on where to look ?
Thanks.

---

### Post by MartynT on 2010-12-30
Some more info ...

At the failure it gives me the option to ignore, skip, etc. or Manual fix.

The Manual option takes me to a shell that reports ...

```
Filesystem check or mount failed
```

A df reveals that only the sdb2 partition (/) is mounted.  sdb1 (/boot) and sdb3 (/home) are not.

That explains the failure, but why is it happening ?

If I reboot from that shell and retry at the grub2 menu, 10.10 loads.

Why would it fail on first try ?

---

### Post by gringo guy on 2011-01-04
Did you figure this out? Funny, but I have nearly an identical setup and, about 5 hours after you first posted this, got exactly the same error after connecting the other two disks. 'Been watching this space, waiting for a reply while doing some other setup stuff (I'm a Ubuntu noob: nearly 3 weeks now, and lovin' it). 

Anyway, last night decided to dig into the [Grub2 docco]("https://help.ubuntu.com/community/Grub2") here in the Community pages, and started comparing with my system. Turns out that my fstab entry for /boot was using /dev/sda1 while both / and /home were using UUIDs. Fixed that, connected up my other two disks, and everything worked.  FWIW, I highly recommend adding unique partition labels to everything--it makes troubleshooting a whole lot simpler, and the 'Places' entries are a lot nicer, too. 
Solo mi dos colones,

---

