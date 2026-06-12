---
title: "Partition Cleanup"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by amanda on 2009-12-11
Soooo: I got a new laptop. I know I'm going to need to use the proprietary OS that came with it so I thought I'd dual boot. I'll skip the shaggy dog story and cut to the chase which is that I'm pretty happy with my machine over all but I've got partitions all over the place and what I'd like to do is clean them up *without* reinstalling. One problem is that a partition which bears the boot flag is actually smack in the middle of some unallocated space. 

I'm not convinced that this partition is really my boot partition but I don't fully understand ... um ... booting. I'd like to understand it better so I can make wise decisions about how to use my space better. Suggestions? 

I'm reading this: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) now. 

Thanks!

```

[0 amanda@luna]$ sudo fdisk -l
[sudo] password for amanda: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaf27f150

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2             193        2639    19648440    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           13755       14593     6735576    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4            2639       13318    85783320    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5            2639       12983    83091928+  83  Linux
/dev/sda6           12983       13318     2691328+  82  Linux swap / Solaris

Partition table entries are not in disk order


```

and also 

```

[0 amanda@luna]$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              78G   21G   54G  28% /
udev                  1.5G  324K  1.5G   1% /dev
none                  1.5G  648K  1.5G   1% /dev/shm
none                  1.5G   92K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/home/amanda/.Private
                       78G   21G   54G  28% /home/amanda

```

---

### Post by phillw on 2009-12-11
> **amanda said:**
> Soooo: I got a new laptop. I know I'm going to need to use the proprietary OS that came with it so I thought I'd dual boot. I'll skip the shaggy dog story and cut to the chase which is that I'm pretty happy with my machine over all but I've got partitions all over the place and what I'd like to do is clean them up *without* reinstalling. One problem is that a partition which bears the boot flag is actually smack in the middle of some unallocated space. 

I'm not convinced that this partition is really my boot partition but I don't fully understand ... um ... booting. I'd like to understand it better so I can make wise decisions about how to use my space better. Suggestions? 

I'm reading this: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) now. 

Thanks!

```

[0 amanda@luna]$ sudo fdisk -l
[sudo] password for amanda: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaf27f150

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2             193        2639    19648440    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           13755       14593     6735576    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4            2639       13318    85783320    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5            2639       12983    83091928+  83  Linux
/dev/sda6           12983       13318     2691328+  82  Linux swap / Solaris

Partition table entries are not in disk order


```and also 

```

[0 amanda@luna]$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              78G   21G   54G  28% /
udev                  1.5G  324K  1.5G   1% /dev
none                  1.5G  648K  1.5G   1% /dev/shm
none                  1.5G   92K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/home/amanda/.Private
                       78G   21G   54G  28% /home/amanda

```

Okies, very quickly. You can have 4 logical or 'parent' extended partitions sda1 - sda3 are Win logical  partitions - at a guess, I'm surmising you have a Win Recovery partition.
sda4 is a 'parent' extended partition. sda5 & sda6 are 'child' partitions of the parent partition. 
Hope that makes some sense to you, it is very basic intro to partitions !!

sda5 (your ubuntu area) reports back that you've used 28% - Any thing below 80% is good. After 80% it's time to think about either some pruning or give it more room. Over 90% is SERIOUS.

As rough calculation, it seems you have 2GB of swap - which is fine if you have 2GB of RAM. The 'loss' of a GB of disk space on your system is not really worth getting the scalpel out for.

Regards,

Phill.

---

### Post by amanda on 2009-12-11
The space won't be an issue for a long time, but it was (is) making me kind of nuts to have such a scattered setup. 

The thing I realized I needed to do was to remove the ntfs partion at /dev/sda2 and re-create it to use the full available space between /dev/sda1 and /dev/sda4. So that was one thing. 

I still have about 6G between some unallocated space after /dev/sda5 but within /dev/sda4 (2.57 GiB) and after /dev/sda4 (3.35 GiB).

I also found the "hidden" flag, which I set on the rescue partition and the "SERVICEV003" partition so I don't have to look at them. 

I'd still like to figure out whether or not /dev/sda1 is really my boot partition and whether I can safely overwrite it.

---

### Post by darkod on 2009-12-11
> **amanda said:**
> 
The thing I realized I needed to do was to remove the ntfs partion at /dev/sda2 and re-create it to use the full available space between /dev/sda1 and /dev/sda4. So that was one thing. 


It doesn't look like there is more space between /dev/sda1 and /dev/sda4. /dev/sda2 is already taking all space between 193 and 2639 and then /dev/sda4 starts.

PS. Also there is no free space inside /dev/sda4, it's taken by / and swap.
Yes, there is some space after /dev/sda4 between 13318 and 13755, and that is all.

---

