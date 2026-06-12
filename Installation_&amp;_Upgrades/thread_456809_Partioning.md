---
title: "Partioning"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by Austag on 2007-05-28
I am wanting to install Ubuntu but first I wanted to ask some questions

My computer is split up with 4 primary partions. I want to run Vista and Ubuntu in separate logical partitions, Is it possible to run Ubuntu in a logical partition?

Thanks in advance

---

### Post by rainforest on 2007-05-28
I bought a new Gateway laptop a couple of weeks ago, pre-loaded with Vista. I made it a dual-boot with Ubuntu.

Just yesterday, I reformatted the whole drive, re-partitioned and re-installed everything. Here's how I broke things up ....

part 1 - 20 GiB NTFS - Vista lives here - primary partition
part 2 - 20 GiB ext3 - Ubuntu lives here - primary partition - mounted on /
part 3 - 4 GiB swap - logical partition
part 4 - 83 GiB ext3 - logical partition - mounted on /home
part 5 - 10 GiB FAT32 - primary partition - mounted on /media/sda4 - also available to Vista

I didn't want to make the FAT32 partition a primary, but I couldn't seem to get the installer to format it otherwise. This partition makes it easy to share a small subset of files between Ubuntu and Vista (for the one app I need that hasn't yet been ported to Linux and doesn't have a Linux equivalent).

-Ray

---

### Post by mannheim on 2007-05-28
> **Austag said:**
> Is it possible to run Ubuntu in a logical partition?


Yes, a logical partition is no problem.

---

### Post by ep2011 on 2007-05-28
On Linux, you can have any partition in either Logical or Primary. This is different that windows, which requires Primary partitions.

I have my Ubuntu in logical for both / and /home and Windows in Primary.

---

