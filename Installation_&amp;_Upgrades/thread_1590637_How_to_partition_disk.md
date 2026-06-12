---
title: "How to partition disk"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by Kauai on 2010-10-08
Hi. Currently I only have Ubuntu installed on my laptop taking up my main drive. I'd like to partition my disk into two separate partitions. Whenever I open up terminal and type fdisk /dev/sda I always get: unable to open /dev/sda despite the fact that System>Administration>Disk Utility shows it as my main device. (/dev/sda1 is the main volume)

Any advice? Thanks. I'm new to Ubuntu so I'm a bit baffled.

Note: When I try to format either the device or volume directly in DIsk Utility, it says they're mounted.

---

### Post by lisati on 2010-10-08
You might have to use a "Live CD" if you want to resize your main Ubuntu partition, as nasty things can happen if you resize a partition that's currently mounted.

---

### Post by Kauai on 2010-10-08
> **lisati said:**
> You might have to use a "Live CD" if you want to resize your main Ubuntu partition, as nasty things can happen if you resize a partition that's currently mounted.

Noted. I actually figured out what was wrong with the above as well, as it seems I was forgetting to do the above in a root terminal.

I was able to access fdisk now.

Now my true tech-illiterate question: What is all this cylinder, sector, etc stuff when setting up a new partition? My HDD is 500gb (488gb accounting for logical/temporary partition) so what do I type if I want to split that in half? I'm assuming each "cylinder" etc accounts for a certain amount of bytes but...not sure.

EDIT; Whenever I try to partition the primary partition it says its already defined. If I select a new number (1-4) it says no free sectors available. Could someone just tell me how to partition?

---

### Post by srs5694 on 2010-10-08
If you want to split the existing partition without damaging it, fdisk is the wrong tool to use; use GParted from a live CD boot to resize the partition and then create a new one. If you use fdisk, you'll delete the old one and create a new, smaller partition, leaving the filesystem it contains unchanged. This will be Bad. Very Very Bad. (There are ways to do it with fdisk, but they involve more work.

As to cylinders, etc., in the old days, disks were addressed using a scheme known as cylinder/head/sector (CHS) addressing, which was basically a way to identify a sector (the lowest level of addressable information on a hard disk, typically 512 bytes of data) via three numbers. Today CHS addressing is a relic of the past, but some utilities, including fdisk, still use it for historical purposes. You can now disable CHS mode in fdisk, and it's generally wise to do so, by typing "u" at the main menu or by launching it with the -u command-line switch.

---

