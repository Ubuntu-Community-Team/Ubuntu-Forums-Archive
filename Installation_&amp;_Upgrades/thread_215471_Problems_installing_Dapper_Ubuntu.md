---
title: "Problems installing Dapper Ubuntu"
date: 2006-07-14
forum: Installation &amp; Upgrades
---

### Post by Heretician on 2006-07-14
It boots up fine to the installation windows, I select the choice "Start or Install Ubuntu" and I get this midway through installing (In a black window with several things scrolling, all say OK for the status)

"Failed to start X server, it is likely that it is not set up correctly. Would you like to view the X Server output and diagnose the problem?"

Alrighty, buncha stuff when I view it, two pages of tons of things..

Reboot PC, go back to Ubuntu Installation window and select "Start Ubuntu in Safe Graphics mode"

Nice, nice! The first time I get to see the Ubuntu desktop on my screen... But; after doubleclicking on Install, it will go through perfectly until it gets to 68% done (43 seconds remaining) I have tried this 3 different times, only once having other programs up and it always stops at the same point. 

The OS will not boot up without the CD so i'm sure it isn't already installed.

Some help please

EDIT:
[http://www.ubuntuforums.org/showthread.php?t=187580](http://www.ubuntuforums.org/showthread.php?t=187580)
Seems that they are having the same kind of problem as myself, although mine is a bit worse.

---

### Post by swamytk on 2006-07-14
What is your hardware? CPU/RAM/HDD

---

### Post by Heretician on 2006-07-14
Intel 3 ghz
2 gb ram
80gb hard drive

---

### Post by swamytk on 2006-07-14
nice h/w... :-)

1. Did you media check your CD? If not worth doing it.
2. Try to disable APIC adn ACPI by passing noapic and acpi=off to kernel
3. Let the Ubuntu installer partition your (empty space or entire hdd) hard disk - I too had problem with partition.

---

### Post by Heretician on 2006-07-14
> **swamytk said:**
> nice h/w... :-)

1. Did you media check your CD? If not worth doing it.
2. Try to disable APIC adn ACPI by passing noapic and acpi=off to kernel
3. Let the Ubuntu installer partition your (empty space or entire hdd) hard disk - I too had problem with partition.

-- 1.) Yes, only one single file errored, it was at the end, I think it said "Mismatch" instead of "OK"

-- 2.) No clue how to do that heheh

-- 3.) I am attempting to format the entire HDD :)

---

### Post by bodhi.zazen on 2006-07-21
Were you ever able to install?

Sounds as if you have a bad disk (it happens sometimes).

Also, although I have not installed Ubuntu recently, my understanding from reading the forums is you should use the "Alternate" instillation disc and not the Live disk (to install Ubuntu).

To disable APIC and ACPI- These will be options at the time of booting the CD. If this option works you will need to modify GRUB.

My, what a large hard drive you have. Ubuntu likely needs no more then 15 GB. Consider partitioning your drive. Options- several 15 GB partitions (can try several versions of Linux) or make a 65 GB "Data" partition. You could mount this as home, but if you are sharing the data partition with several OS I prefer to just mount it as a partition and not home (ie /mnt/Data). Partitioning is more secure and allows you to re-install the OS (if needed) without overwriting your data.

If you still need help let me know.

---

### Post by gigaferz on 2006-07-21
Hi I just Installed ubuntu from the cd..and my problem was the installer frezing during the pertition porcess...so..before that search on the net for [http://www.psychocats.net/](http://www.psychocats.net/) then  use the partition editor from the live cd..make your partitions and try again (restart after making the partitions)..

If that fails *dont install* it Until you figure out the problem using the livecd...cause last time I tried installing the last version i messed up my computer...I think if you have problems with the live cd its morelikely that youll get the same problems with the installation on your hard drive..I burned a few discs..kubuntu ,ubuntu live,,and I have an Installation disc..If you live in the us I can mail it to you...good luck..

---

