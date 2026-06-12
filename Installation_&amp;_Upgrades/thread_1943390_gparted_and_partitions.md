---
title: "gparted and partitions"
date: 2012-03-19
forum: Installation &amp; Upgrades
---

### Post by sefs on 2012-03-19
Hi there I just created the following partitions.  Is I get one warning but look at the starts and ends.  The following partition begins exactly where the preceding one ends, as if they are overlapping.  I used gparted 0.12.0-5.  Is that normal? Can writing to one partition overwrite data in the other where they overlap according to the fdisk printout below?

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        2563    20480000   83  Linux
/dev/sda3   *        2563        5113    20480000    7  HPFS/NTFS
/dev/sda4            5113       60802   447323136    5  Extended
/dev/sda5            5113       24745   157696000   83  Linux
/dev/sda6           24745       59758   281237504   83  Linux
/dev/sda7           59758       60802     8386560   82  Linux swap / Solaris

```

---

### Post by darkod on 2012-03-19
This is because they don't end on cylinders, as the message says.

For example, the End and Start are on cylinder 13 but that doesn't mean overlapping by itself, there are many sectors on that cylinder.

For more precise results, you can print the parted info with units in sectors:

sudo parted /dev/sda unit s print

When using sectors the Start/End should not overlap if I am not mistaken.

---

### Post by coffeecat on 2012-03-19
@sefs, you would have used "sudo fdisk -l" in Ubuntu 11.04 or earlier to have got an output in cylinders. Measuring partition boundaries in cylinders is of little or no practical use. When running fdisk in 11.04 or earlier, use "sudo fdisk -lu" to get the output in sectors. If you do so you'll find that there are no overlapping partitions, otherwise fdisk would have told you so. 

In Ubuntu 11.10 and later, "sudo fdisk -l" now defaults to sectors (and not before time). It will also default to sectors with "sudo fdisk -lu" unless you tell it to report in cylinders. See man fdisk for whichever version of fdisk/Ubuntu you are using for more.

---

### Post by sefs on 2012-03-19
Yes, I checked you are both correct and, yup I am on an Ubuntu earlier than 11.04.

Thanks.

**Update:**
Adding c masks the warnings also by turning off dos compatibility it seems.

e.g.
```

sudo fdisk -luc

```

---

