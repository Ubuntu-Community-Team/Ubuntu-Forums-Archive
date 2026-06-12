---
title: "swap file"
date: 2007-09-18
forum: Installation &amp; Upgrades
---

### Post by scottym on 2007-09-18
I have just upgraded to Ubunto  7.04  and my swap file is not working even though I have a swap partition. It workedfine with 6.06 so I don't understand what is occurring since I kept my old partitions and only formatted the / and the /swap partitions for the new install.
This is how I am partitioned:

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1779    14289786   83  Linux
/dev/sda2            1780        1795      128520   83  Linux
/dev/sda3            1796        2350     4458037+  83  Linux
/dev/sda4            2351        2432      658665   82  Linux swap / Solaris


 The free command yields:

            total       used       free     shared    buffers     cached
Mem:        636412     584392      52020          0      42844     279848
Low:        636412     584392      52020
High:            0          0          0
-/+ buffers/cache:     261700     374712
Swap:            0          0          0

or free -t -m:

             total       used       free     shared    buffers     cached
Mem:           621        570         50          0         41        273
-/+ buffers/cache:        255        365
Swap:            0          0          0
Total:         621        570         50

i have tried to activate the sawp by using gparted and also the swapon command but nothing has worked so far. Any ideas are welcome.

---

### Post by Jussi Kukkonen on 2007-09-18
I'm guessing there's a UUID mixup in your /etc/fstab. Please paste the output of these commands here:```

cat /etc/fstab
blkid
```

---

### Post by scottym on 2007-09-18
Thanks for helping. Here's the info 
Cat:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=d1856a7b-0d67-4613-bc4c-d9a13f370a21 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=44a09475-9391-41e3-9bff-d801ad74260c /boot           ext3    defaults        0       2
# /dev/sda1
UUID=0229e0b7-a13c-4955-9253-08384e2ee930 /home           ext3    defaults        0       2
# /dev/sda4
UUID=12bcec6d-d477-412d-a490-d9269f45567c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

blkid

/dev/sda1: UUID="0229e0b7-a13c-4955-9253-08384e2ee930" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="44a09475-9391-41e3-9bff-d801ad74260c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="d1856a7b-0d67-4613-bc4c-d9a13f370a21" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="4eb79727-8790-4d76-ba46-f224f6b00439" TYPE="swap"

---

### Post by dcstar on 2007-09-18
> **scottym said:**
> I have just upgraded to Ubunto  7.04  and my swap file is not working even though I have a swap partition. It workedfine with 6.06 so I don't understand what is occurring since I kept my old partitions and only formatted the / and the /swap partitions for the new install.
..........
i have tried to activate the sawp by using gparted and also the swapon command but nothing has worked so far. Any ideas are welcome.

What does "swapon -s" show?

---

### Post by dabl on 2007-09-18
How much free disk space is available in "/" and "/boot"?

You say swap is "not working" -- what do you mean?  Are you running out of memory for running processes?  Or are you simply observing that swap is not being used?

---

### Post by scottym on 2007-09-18
When I say the swap partition is not working I mean that it is not loading. The free command yields 0 swap available. The partitions are exactly the same as with Ubuntu 6.06 where it functioned. I could see it in system monitor. Now system monitor says 0 space in use.


This is what I get with swap -s before using gparted to enable the swap partition:

~$ swapon -s
Filename                                Type            Size    Used    Priority

After gparted to enable partition:
~$ swapon -s
Filename                                Type            Size    Used    Priority
/dev/sda4                               partition       658656  0       -1

However, after booting it will revert to the first option.

---

### Post by dabl on 2007-09-18
If I'm reading your output correctly, the UUID for the swap partition listed in your fstab file is different than the UUID listed in the blkid output.

fstab says "UUID=12bcec6d-d477-412d-a490-d9269f45567c"

blkid says /dev/sda4: UUID="4eb79727-8790-4d76-ba46-f224f6b00439"

So, I vote for blkid.  Change the fstab entry to match the "..0439" number, and I'll bet you're good to go.

:guitar:

---

### Post by scottym on 2007-09-18
dabl, wow, that worked. It so happened that it was time to do a forced check of the drive so the status screen during bootup displayed the results of the swap and swap file with ok. The free command shows that swap is now available but none is in use. 

With Edgy it was always using around 40%. Does Feisty use swapping more efficiently?   

Thanks again for your help,
Scotty

---

### Post by dabl on 2007-09-18
Cool -- glad you're fixed.

It might help others in the future if you'll mark the subject/title "CLOSED", please and thank you.



I've got 4GB of RAM, and have never seen my system use any swap at all -- I think you have to have less than 1GB of RAM to get any swap action going -- it also depends on what you're doing.  :)

---

### Post by MONODA on 2008-03-28
yeah but sometimes you need it eg hibernation

---

