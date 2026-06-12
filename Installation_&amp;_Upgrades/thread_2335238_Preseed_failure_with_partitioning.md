---
title: "Preseed failure with partitioning"
date: 2016-08-26
forum: Installation &amp; Upgrades
---

### Post by jdh239 on 2016-08-26
Summary:  I think I am close.  I think I just need a couple of parameters, but something must be off on my partitioning as seen below.  Thanks in advance for your help.

Environment:  14.04 with two identical SSDs
Goal:  
Create 12 GB swap on each ssd (as sda2) --no raid
Take remaining space, RAID 1 it across both disks (as sda1), format with ext4 (no lvm), mount to /

Here is what I have so far:
```

#===========================================================================================
# PARTMAN PARTITIONING SECTION START
#===========================================================================================

d-i partman-auto/method string raid
d-i partman-auto/disk string /dev/sda /dev/sdb

d-i partman-auto/expert_recipe string \
      raid-partitioning ::                                           \
              20000 40000 -1 raid                                    \
                      $primary{ } $bootable{ } method{ raid }        \
              .                                                      \
              4096 8192 12288 linux-swap                             \
                      $primary{ } method{ swap } format{ }           \
              .

d-i partman-auto-raid/recipe string \
    1 2 0 ext4 /                    \
          /dev/sda1#/dev/sdb1       \
    .                               \

d-i partman-md/confirm boolean true
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true

#===========================================================================================
# PARTMAN PARTITIONING SECTION END
#===========================================================================================

```

======================
Result:
1.  Installer prompts me to remove existing software RAID (I wish for it to never prompt)
2.  Installer prompts again to have changes written to disk (partitioning) before the RAID can be configured.  Again, I wish for it to never prompt.  NOTE:  It has swap setup as partition 2 on both sda and sdb (which is correct)
3.  Dies with: "An unexpected error occurred while setting up a preseeded RAID configuration"

Virt console 4 shows:
[IMG]http://theharmonfam.com/download/ubuntu/20160826_133517.jpg[/IMG]

---

### Post by jdh239 on 2016-08-26
I fixed it.  Here is my working setup:

```

d-i partman-auto/method string raid
d-i partman-auto/disk string /dev/sda /dev/sdb

# <raidtype> <devcount> <sparecount> <fstype> <mountpoint> <devices> <sparedevices>
d-i partman-auto/expert_recipe string \
      root-swap ::                                                      \
              10000 40000 -1 raid                                       \
                      $primary{ } $bootable{ } method{ raid } format{ } \
              .                                                         \
              1024 8192 12288 linux-swap                                \
                      $primary{ } method{ swap } format{ }              \
              .

d-i partman-auto-raid/recipe string \
    1 2 0 ext4 /                    \
          /dev/sda1#/dev/sdb1       \
    .

d-i partman-md/device_remove_md boolean true
d-i partman-md/confirm boolean true
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true



```

---

