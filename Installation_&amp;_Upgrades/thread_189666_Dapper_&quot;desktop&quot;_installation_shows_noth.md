---
title: "Dapper &quot;desktop&quot; installation shows nothing in partitioner"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by flabbah on 2006-06-05
Hello,

I was installing Dapper on a machine with only one hard drive, (/dev/hda) and one primary partition on that hard drive (LVM physical volume).

I booted the "Desktop" installation CD and got to the step

"Prepare disk space"
> Erase entire disk
> Manually edit partition table

If I click on "Manually edit partition table", then "Forward", the window then says "Prepare Partitions" with a greyed-out partitioner area as a progress-bar bar-thingy moves back and forth.

Then the progress bar goes goes away, along with the greyed-out partitioner, showing only the window:

* * * 

Prepare Partitions
Make sure to allocate space ....

Step 5/6

* * * 

Clicking on Forward does absolutely nothing.

I think the partitioner was supposed to display here, but something is totally borked.

I've had a lot of problems with both the desktop / alternate installer using LVM - I think this things needs some more testing.

-Alex

---

### Post by steigers on 2006-09-18
I had the same problem: A couple of partitions created in Windows XP with Partition Magic, but the Kubuntu manual selection of the partition during installation remained blank. What helped in my case was to remove the three Linux-partitions I created with QTPart and recreate it.

---

