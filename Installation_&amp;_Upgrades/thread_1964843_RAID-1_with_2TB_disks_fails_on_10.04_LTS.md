---
title: "RAID-1 with 2TB disks fails on 10.04 LTS"
date: 2012-04-24
forum: Installation &amp; Upgrades
---

### Post by ajaymahagaokar on 2012-04-24
Hello,
 
 
I am trying to use preseed to do automated install of 10.04 LTS server. The
system needs RAID-1 with no spares on 2 disks. I set this up in the preseed.cfg
file and it works fine for VM, 500GB, 750GB & 1TB disks, but fails to install on
2TB disks. The error message is "This GPT partition label has no BIOS Boot Partition; 
embedding won't be possible!."
 
 
The partition part of the preseed.cfg is:
 
 
#### Start
d-i partman-auto/method string raid
# If one of the disks that are going to be automatically partitioned
# contains an old LVM configuration, the user will normally receive a
# warning. This can be preseeded away...
# This makes partman automatically partition without confirmation.
d-i partman-partitioning/confirm_resize boolean true
# Write the changes to the storage devices and configure RAID?
d-i partman-md/confirm boolean true
# Write a new empty partition table?
d-i partman-partitioning/choose_label string msdos
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/confirm_write_new_label boolean true
# Remove existing software RAID partitions?
d-i partman-md/device_remove_md boolean true
d-i partman/choose_partition select finish
d-i partman/confirm_nooverwrite boolean true
# Write the changes to disks?
d-i partman/confirm boolean true
d-i partman-auto/disk string /dev/sda /dev/sdb
d-i partman-auto/method string raid
d-i partman-auto/expert_recipe string \
multiraid :: \
4096 5000 8192 raid \
$primary{ } \
method{ raid } \
. \
2048 2048 200% raid \
$primary{ } \
method{ raid } \
. \
4096 6000 92160 raid \
$primary{ } \
method{ raid } \
. \
1000 1000 -1 raid \
$primary{ } \
method{ raid } \
.
d-i partman-auto-raid/recipe string \
1 2 0 ext4 / \
/dev/sda1#/dev/sdb1 \
. \
1 2 0 swap - \
/dev/sda2#/dev/sdb2 \
. \
1 2 0 ext4 /var \
/dev/sda3#/dev/sdb3 \
. \
1 2 0 ext4 /data \
/dev/sda4#/dev/sdb4 \
.
d-i partman-md/confirm_nooverwrite true
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition \
select Finish partitioning and write changes to disk
d-i partman/confirm boolean true
d-i mdadm/boot_degraded boolean true
#### End
 
 
I tried to circumvent this issue by:
 
 
1. Avoiding GPT: Since 2TB disks are supported under the legacy partition
table (using MBR), forcing an msdos partion should work. To do this I 
used the debian installer idiom "d-i partman-partitioning/choose_label string msdos", 
but the partitioning logic seems to ignore or override it.
 
 
2. Since I am forced to use GPT, I tried to leave some sapce for grub
using Colin Watson's reco (google searched) by inserting the following
line just below the "multiraid:" label in the expert_recipe above.
1 1 1 free $iflabel{ gpt } $reusemethod{ } method{ biosgrub } .\
But unfortunately that does not seem to work either (never get past
the md3 device formatting or resyncing). This may be more to do with the
rev of utils and debian installer in Ubuntu 10.04 LTS.
 
 
Any help with this is greatly appreciated.
 
 
Thanks,
 
 
Ajay

---

### Post by gordintoronto on 2012-04-24
In two days 12.04 will be released, and I expect it to be much better at dealing with GPT than 10.04.

---

### Post by ajaymahagaokar on 2012-04-26
Thanks for the reply, but unfortunately, that is not an option - our product is based on 10.04 and this would throw a major qa cycle.

Any idea why I cannot force the partition table type to be "msdos"?

Ajay

---

### Post by nariub on 2012-04-26
depending on your hardware you may not be able to boot a GPT partition.

I installed onto a 2TB raid-1 by cutting it into an OS and HOME
I have an old Dell Dimension E5150/E510 with ICH7R
I used the Intel sw in the bios to cut my 2TB drives into two VirtualDrives
OS = 160GB (as a RAID1 across both drives)
HOME= Rest of the 2TB (as a RAID1 across both drives)
and I boot from the ext4 OS drive

older hardware such as mine will not boot GPT partitions and the old MBR doesn't support 
2TB drives.   you need an ECFI?? to boot 2TB GPTs

---

### Post by nariub on 2012-05-03
> **nariub said:**
> depending on your hardware you may not be able to boot a GPT partition.

I installed onto a 2TB raid-1 by cutting it into an OS and HOME
I have an old Dell Dimension E5150/E510 with ICH7R
I used the Intel sw in the bios to cut my 2TB drives into two VirtualDrives
OS = 160GB (as a RAID1 across both drives)
HOME= Rest of the 2TB (as a RAID1 across both drives)
and I boot from the ext4 OS drive

older hardware such as mine will not boot GPT partitions and the old MBR doesn't support 
2TB drives.   you need an ECFI?? to boot 2TB GPTs

My bad .. not ECFI but (U)EFI
there is an article about it here[  http://ubuntuforums.org/showthread.php?t=1958383]("http://ubuntuforums.org/showthread.php?t=1958383")
called **GUIDE: (U)EFI installation**

---

