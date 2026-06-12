---
title: "Ubiquity  &amp; RAID Remnants"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by jv2112 on 2009-12-11
I am installing Karmic on a drive that use to be part of a RAID array on a different computer. The install still picks it up as a RAID drive and ubiquity crashes while trying to partition. I have formatted, deleted partition and now running bad blocks (sudo badblocks -VSW /dev/sda1) on it to completely erase. I have also removed DMRAID prior to install and I keep hitting a wall.

Any Ideas ?:(> 

---

### Post by presence1960 on 2009-12-11
> **jv2112 said:**
> I am installing Karmic on a drive that use to be part of a RAID array on a different computer. The install still picks it up as a RAID drive and ubiquity crashes while trying to partition. I have formatted, deleted partition and now running bad blocks (sudo badblocks -VSW /dev/sda1) on it to completely erase. I have also removed DMRAID prior to install and I keep hitting a wall.

Any Ideas ?:(

how did you get rid of RAID? This is how I did it:

To get rid of it, Open a terminal and type ```
dmraid -E -r /dev/name_of_your_disk
```

for name of your disk substitute sda, sdb, sdc, etc as it applies to your partition table.

If that is how you did it sorry I could not help.

---

### Post by jv2112 on 2009-12-13
Awesome ! Thank You for the help !!!!

---

### Post by presence1960 on 2009-12-13
> **jv2112 said:**
> Awesome ! Thank You for the help !!!!

Glad you got it working. Enjoy (K)ubuntu

---

