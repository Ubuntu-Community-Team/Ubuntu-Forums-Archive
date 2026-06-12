---
title: "Can't partition hard drive or write to it - won't install"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by leas on 2008-03-04
I'm new to Linux - but I tried almost every version and every boot partition, and my hard drive cannot be written to! It worked fine in windows xp, which now was erased and won't start. The install went about half way, then said it couldn't write to part of the drive. I don't think there is a problem with the drive, because it worked fine in windows.

GParted finds the partition, and marks "unallocated", but when I try to partition, it fails.

Anyone know of a utility I can use to partition this hard drive that will tell me what's wrong? 

Thanks!

---

### Post by housam on 2008-03-04
Maybe your HDD have a bad sector or more. try to reformat the entire HDD and repartition it again using Gparted.

---

### Post by az on 2008-03-04
[http://help.ubuntu.com/community/FaultyHardware](http://help.ubuntu.com/community/FaultyHardware)

Use SMART to see of the drive has logged some errors in the past.  Run a SMART self-test.

---

