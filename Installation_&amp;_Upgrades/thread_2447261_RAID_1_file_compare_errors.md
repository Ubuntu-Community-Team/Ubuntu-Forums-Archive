---
title: "RAID 1 file compare errors"
date: 2020-07-15
forum: Installation &amp; Upgrades
---

### Post by hrubin996 on 2020-07-15
I have a Ubuntu mate installation with 2 raid 1 arrays of 4GB each (total 4 4GB drives, Raid arrays were created with mdadm)

When I copy l(using caja) arge files from either raid array to another disk and then compare the original files to the copies, meld and diff report many compare errors.  It seems unlikely that both raid arrays would have bad disks. And I get the same results with more than 1 disk.

Is there any way to diagnose or fix the problem is, or should I just build another $2K machine and salvage the hardware in this one?

Motherboard [GIGABYTE Z390 UD LGA 1151]("https://www.newegg.com/p/N82E16813145095?Item=N82E16813145095")
Boot drive [Samsung 960 EVO 500GB Solid State Drive]("https://www.amazon.com/gp/product/B01M20VBU7/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1")
CPU [URL="https://www.newegg.com/core-i7-8th-gen-intel-core-i7-8700k/p/N82E16819117827?Item=N82E16819117827"]Intel Core i7-8700K Coffee Lake 6-Core 3.7 GHz
[/URL]64GB RAM [G.SKILL Aegis 32GB (2 x 16GB) 288-Pin DDR4]("https://www.newegg.com/g-skill-32gb-288-pin-ddr4-sdram/p/N82E16820232765?Item=N82E16820232765")
4 Drives [WD Red Pro WD4003FFBX 4TB 7200 RPM]("https://www.newegg.com/red-pro-wd4003ffbx-4tb/p/N82E16822234345?Item=N82E16822234345")
Power [URL="https://www.newegg.com/seasonic-focus-750-gold-ssr-750fm-750w/p/N82E16817151201?Item=N82E16817151201"]Seasonic FOCUS GM-750, 750W 80+ Gold
[/URL]Ubuntu mate 18.04.4

---

### Post by ActionParsnip on 2020-07-16
Are the drives healthy?

---

### Post by hrubin996 on 2020-07-16
@ActionParsnip said "Are the drives healthy? 				"

Thanks for the reply.
Yes, /usr/bin/gnome-disks reports "Disk is OK" for all 4 drives.

---

### Post by TheFu on 2020-07-16
Try using other tools for the copy - cp, rsync, some other GUI thingy.
Is the target **file system** the same type?  

Could be a failing disk controller or bad cables.  Are all the RAID devices connected to the same controller?  Do they share an interconnect?  eSATA, USB, Infiniband - all in a single cable?

Basically, _simplify and test_ over and over to eliminate different parts to the "file copy" process.  Swap out the parts that can easily be swapped.   Simplify and test.

---

### Post by hrubin996 on 2020-07-18
Thanks for the reply and your questions, @TheFu

1) I tried using cp to copy the files with no improvement
2) All 4 RAID devices are connected to the same controller on the Motherboard [GIGABYTE Z390 UD LGA 1151]("https://www.newegg.com/p/N82E16813145095?Item=N82E16813145095")
3) They do not share an interconnect
4) Each of the 4 physical hard drives in the 2 RAID1 arrays has its own SATA cable

What they have in common:

All 4 physical hard drives are connected to the same Motherboard [GIGABYTE Z390 UD LGA 1151]("https://www.newegg.com/p/N82E16813145095?Item=N82E16813145095")
All 4 physical hard drives are Western Digital [WD Red Pro WD4003FFBX 4TB 7200 RPM]("https://www.newegg.com/red-pro-wd4003ffbx-4tb/p/N82E16822234345?Item=N82E16822234345")
RAID arrays were created with mdadm on Ubuntu mate 18.04.4

---

### Post by hrubin996 on 2020-08-11
Thanks for the replies.  I spent the $$$ and built a new machine and it had the same problem.

It turns out there's a linux RAID website and mailing list at
[https://raid.wiki.kernel.org/index.php/Linux_Raid](https://raid.wiki.kernel.org/index.php/Linux_Raid)

where I'll continue this discussion

---

### Post by TheFu on 2020-08-11
> **hrubin996 said:**
> @ActionParsnip said "Are the drives healthy? 				"

Thanks for the reply.
Yes, /usr/bin/gnome-disks reports "Disk is OK" for all 4 drives.

Use smartctl to see the true SMART data.  "Disk is OK" doesn't mean what most people think it means.

---

### Post by hrubin996 on 2020-09-18
memtest86+ revealed that I had a bad stick of RAM [G.SKILL Aegis 32GB (2 x 16GB) 288-Pin DDR4]("https://www.newegg.com/g-skill-32gb-288-pin-ddr4-sdram/p/N82E16820232765?Item=N82E16820232765")
G.Skill had reasonably fast warranty turnaround and everything is OK now.

---

