---
title: "Partitions by Installer"
date: 2012-08-01
forum: Installation &amp; Upgrades
---

### Post by Ron O on 2012-08-01
Wanting to compare 12.04 32 bit and 64 bit, I had 32 bit installed on the primary partition sda1. The remainder of the drive was unallocated space except for a small swap file in its own primary partition. When I installed 64 bit using the regular live CD (not the Alt CD), the installer created an extended partition and put the files on sda5 within the extended partition- see screenshot.

Question: WHY did the installer use an extended partition when all it contains is a single sda5 partition? (No swap file within- both installations are using the swap file in the primary sda2 partition without any problems.) I was expecting to see another primary partition, not an extended one.

sda1 (the 32 bit installation) will be deleted since the 64 bit install is so much faster. So I will be left with my 64 bit installation inside of an extended partition that looks useless to me.

Questions: Is there a disadvantage to this setup? Should I reformat the whole drive and put the 64 bit install in a primary partition before I do any further work? Will the live CD even let me do this, or will it take control again and create another extended partition with no benefit that I can see?

I did not notice any partitioning options with the installer in this live CD like I have seen in the ALT CD I have used on older installations. Maybe I missed it?

---

### Post by darkod on 2012-08-01
The option to partition manually (install manually) is under the Something Else option, you missed it.

It creates a logical partition instead of primary so that you can still create new partitions in the future if you want to. If it created the partition as primary it would have been three partitions, which is close to the limit of 4 primary partitions.

There is no disadvantage of the root partition being a logical instead of primary.

---

### Post by Ron O on 2012-08-02
Thanks. I thought that perhaps the boot loader would have issues with only an extended partition for the main OS rather than a primary partition.

I found out the hard way about the 4 primary limit when I put Ubuntu on a netbook where Asus had all 4 partitions in use (Express Gate and other junk). I shut off Windows 7 auto-backup and formatted the backup partition for Ubuntu, recovering half of the system hard drive that was just sitting there waiting for Windoze to back itself up.

---

