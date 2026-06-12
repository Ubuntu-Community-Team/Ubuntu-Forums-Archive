---
title: "Ubuntu 12.04 Auto Installation Error for  No root file system"
date: 2012-10-25
forum: Installation &amp; Upgrades
---

### Post by joey741019 on 2012-10-25
I use preseed.cfg to partition the disk
and almost like 70% will show the error such like download below
 
```

No root file system
No root file system is defined.
Please correct this from the partitioning menu.

```
 
but sometimes likes 30% finished installation without error and anything is fine
 
what's wrong with my perseed.cfg
 
It's my preseed.cfg
 
```

d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string lvm
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-md/device_remove_md boolean true
d-i partman-lvm/confirm boolean true
d-i partman-auto-lvm/new_vg_name string CSIEHadoop
d-i partman-auto-lvm/guided_size string max
d-i partman-auto/expert_recipe string           \
 boot-root ::                                   \
 200 50 200 ext2                                \
 $primary{ } $bootable{ }                       \
 method{ format } format{ }                     \
 use_filesystem{ } filesystem{ ext2 }           \
 mountpoint{ /boot }                            \
 .                                              \
 3072 10000 3072 ext4 method{ lvm }             \
$lvmok{ } method{ format } format{ }           \
 use_filesystem{ } filesystem{ ext4 }           \
 mountpoint{ / }                                \
 .                                              \
 3072 10000 1000000000 ext4 method{ lvm }       \
 $lvmok{ } method{ format } format{ }           \
 use_filesystem{ } filesystem{ ext4 }           \
 mountpoint{ /var/lib/hadoop }                  \
 .                                              \
 1024 1024 1024 linux-swap                      \
 method{ swap } format{ }                       \
 .
d-i partman/default_filesystem string ext4
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true
d-i partman-lvm/confirm_nooverwrite boolean true
d-i partman-lvm/confirm boolean true
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-lvm/confirm_nooverwrite boolean true

```

---

### Post by dino99 on 2012-10-25
why using such complicated way ?

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

---

### Post by joey741019 on 2012-10-26
It's any wrong with my config?

---

