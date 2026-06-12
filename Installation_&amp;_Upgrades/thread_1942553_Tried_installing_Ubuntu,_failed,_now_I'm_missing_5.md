---
title: "Tried installing Ubuntu, failed, now I'm missing 50GB"
date: 2012-03-17
forum: Installation &amp; Upgrades
---

### Post by Jiazzz on 2012-03-17
I tried installing Ubuntu 11.10 on my new laptop (HP Pavilion dv6-6b20SE). I didn't want to do a complete re-install and pre-partitioning my hard disk, so I tried shrinking my main NTFS partition (which was about 620GB + recovery and system partitions) and partitioning the unallocated space, using the Ubuntu setup. It then showed the 50GB I tried to shrink was unusable to allocate, so I expanded the NTFS partition back to its original size. Not wanting to give up, I tried it again. Again, it said it was unusable, so I expanded again. After rebooting, and booting up in Win7, I noticed about 50GB missing from my C: partition. It cannot be found with disk manager or GParted.

---

### Post by darkod on 2012-03-17
Can you post an image of Disk Management and/or Gparted?

It can't go missing. Maybe it's just left as unallocated space not belonging to any partition.

HP usually ships laptops with all 4 primary partitions used. That's why even if you have unallocated space, ubuntu can't install because 4 primary partitions are the maximum, it can't create more.

And don't try too many times, you can get into trouble.

You can consider deleting one of the Restore or HP Tools partition. Never delete the System Reserved partition of win7. You can create restore DVDs with the restore software on your laptop and then you don't need the restore partition any more. Plus you can use that space if you delete it.

---

### Post by Jiazzz on 2012-03-18
Somehow Ubuntu now does recognize the partition as being 623GB, but Windows7 still displays it as 578GB

---

### Post by coffeecat on 2012-03-19
> **Jiazzz said:**
> Somehow Ubuntu now does recognize the partition as being 623GB, but Windows7 still displays it as 578GB

623 GB ([Gigabytes]("http://en.wikipedia.org/wiki/Gigabyte")) = 580.2 GiB ([Gibibytes]("http://en.wikipedia.org/wiki/Gibibyte")), so my guess is the discrepancy could be due to the two figures being in different units.

As far as I remember, Windows 7 Disk Management reports sizes in GiB but calls them GB, whereas Gparted in Ubuntu reports in GiB and also calls them GiB. So if you are indeed seeing size reported as GB in Ubuntu, then that would not have been in Gparted. I *thought* Ubuntu had standardised on all GiB values, but I may be wrong, Where did you see the figure 623 in Ubuntu, and where 578 in Windows?

To go back to your original problem, darkod has pointed out an important issue - that HP has used up all your allowance of four primary partitions. Even if you shrink a partition, the unallocated space cannot be used until you delete one of the existing primary partitions. So that we can help you with sorting this all out, including partition sizes, boot up your Ubuntu 11.10 live CD or USB and post the output of this terminal command:

```
sudo fdisk -lu
```

For completeness, also please open Gparted and post a screenshot of the open window showing your partition layout. Press Alt+PrintScr to get a screenshot of an open window.

---

