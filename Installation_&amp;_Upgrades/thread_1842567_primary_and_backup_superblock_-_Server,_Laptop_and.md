---
title: "primary and backup superblock - Server, Laptop and VMware"
date: 2011-09-11
forum: Installation &amp; Upgrades
---

### Post by Ruy Benton on 2011-09-11
Hi,
 
I have a UBUNTU 11.04 with two ext4 partitions. (I tested this env. in Server, Laptop and VMware).

And I fsck the unmounted part. to see if everything is ok.

"fsck.ext4 -n /dev/sda1" and everything ok.;)

Next step "dumpe2fs /dev/sda1" and I read the backup superblock.

"fsck.ext4 -n -b 32768 /dev/sda1"                  (block size 4096)

and lots of Free block wrong and 
"Group descriptor xxxxx checksum is invalid.  IGNORED.":confused:



Start with lots of different live distribution and tested /dev/sda1. The same behaviour (Partedmagic, Suse, Fedora).

Why the first (0) Superblock is ok ... with a backup ... lots of error?

Best regards,
Ruy

---

