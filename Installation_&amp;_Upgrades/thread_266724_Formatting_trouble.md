---
title: "Formatting trouble"
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by Vivek788 on 2006-09-27
I have a 37.1 gb hard disk.In that i had given 8.5 GB to linux.
My partition table are like this:
/dev/hda1-9.77gb-ntfs
/dev/hda5-9.77gb-ntfs
/dev/hda6-9.77gb-ntfs
/dev/hda7-1.01gb-linux-swap
/dev/hda8-4.14gb-ext3
unallocated 2.85

the unallocated was created recently as i gave only 4.14 gb to my mandrake instlalation.I had planned to install Dapper in the 2.85.In the installatin of Dapper,when i format the last 2.85 gb to ext3,it is not seen in the next page,where i have to selct he mout point.
When i go back to the partition table, find that 2.85gb with a black border ad a black logo of "unidentified".When i right click it,it shows some errors like "bad filesystem" or"faulty filesystem"

I tried many things,like making another swap.Nothing seems to work.

---

### Post by Vivek788 on 2006-09-29
sorry i found answer in READ BEFORE POSTING!But one doubt remains,should i rebot after gpart before instlalation?

---

### Post by wkulecz on 2006-09-29
Its safest to reboot, but I've skipped this step when using Linux fdisk for years and never had a problem.

--wally.

---

