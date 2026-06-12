---
title: "Planning Server Install -- RAID Strategy"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by schizophant on 2012-10-22
In the near future, I'll be configuring a file server/NAS to run on my work-from-home network. Budget currently necessitates that I limit storage to a single 1TB disc, but I'd like the ability to expand to 2TB in the future via a Level 0 RAID. If I go through the installation and set up a RAID 0, will I be able to easily add storage to the array in the future? Thanks in advance.

---

### Post by darkod on 2012-10-22
First of all, are you aware that raid0 does not offer any redundancy protection? If one disk goes, all data is gone. I hope you consider at least raid1 instead of raid0.

As for the direct question, I don't think you can configure a raid0 array with a missing disk. This is because raid0 doesn't tolerate missing disks at all. raid1 and raid5 array for example, can keep on working with one disk dead (missing), and you can configure the arrays and add a disk later.

But the nature of raid0 is that is saves data 50-50 on both disks, so it can't really work as raid0 on only one disk.

So, I don't think you can do a missing disk with raid0.

PS. When I wrote the above I assumed we are talking about mdadm software raid. With fakeraid (bios raid) or hardware raid it would depend on the card and the options it offers. I don't think a controller card would allow you to configure even a raid1 with a missing disk. mdadm does offer that option, I am not sure about hardware cards and fakeraid.

---

