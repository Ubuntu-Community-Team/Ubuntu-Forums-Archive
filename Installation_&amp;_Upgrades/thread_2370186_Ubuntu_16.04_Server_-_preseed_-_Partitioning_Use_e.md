---
title: "Ubuntu 16.04 Server - preseed - Partitioning: Use entire disk"
date: 2017-08-31
forum: Installation &amp; Upgrades
---

### Post by kokster2 on 2017-08-31
Hello everyone.

I am trying to create a semi-unattended Ubuntu 16.04 Server installation. It all works well up to the point of partitioning.
My goal for partitioning is:

[LIST]
[*]Skip the menu where user selects Guided (with all the different types) and Manual. Instead, I would like to always have 'Guided - use entire disk'
[*]Show the user all disks, so he can choose which one to use
[*]Automatically create all the partitions on that disk, with a help of a recipe available in the preseed
[/LIST]

Currently, I have the following inside my preseed file, with regards to partitioning:

```
# In addition, you'll need to specify the method to use.
# The presently available methods are:
# - regular: use the usual partition types for your architecture
# - lvm:     use LVM to partition the disk
# - crypto:  use LVM within an encrypted partition
d-i partman-auto/method string regular


d-i partman-auto/init_automatically_partition select Guided - use entire disk


# If one of the disks that are going to be automatically partitioned
# contains an old LVM configuration, the user will normally receive a
# warning. This can be preseeded away...
d-i partman-lvm/device_remove_lvm boolean true
# The same applies to pre-existing software RAID array:
d-i partman-md/device_remove_md boolean true
# And the same goes for the confirmation to write the lvm partitions.
d-i partman-lvm/confirm boolean true


# You can choose one of the three predefined partitioning recipes:
# - atomic: all files in one partition
# - home:   separate /home partition
# - multi:  separate /home, /usr, /var, and /tmp partitions
d-i partman-auto/choose_recipe select atomic


d-i partman-auto/expert_recipe string             \
        1 1 1 free                                \
            $bios_boot{ }                         \
            method{ biosgrub }                    \
        .                                         \
        256 40 256 fat32                          \
            $primary{ }                           \
            $lvmignore{ }                         \
            method{ efi }                         \
            format{ }                             \
        .                                         \
        4096 4096 4096 linux-swap                 \
            method{ swap } format{ }              \
        .                                         \
        100 10000 100000000 ext4                  \
            $primary{ }                           \
            method{ format } format{ }            \
            use_filesystem{ } filesystem{ ext4 }  \
            mountpoint{ / }                       \
        .
# This makes partman automatically partition without confirmation.
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish


# Ask user if existing partitions need to be removed!
d-i partman/confirm boolean true
#d-i partman-md/confirm boolean false
#d-i partman-lvm/device_remove_lvm boolean false
d-i partman/confirm_nooverwrite boolean true
#d-i partman-md/confirm_nooverwrite boolean false
#d-i partman-lvm/confirm_nooverwrite boolean false

```

However, with this configuration, I am not given the choice which disk to use (I guess the first disk is always used).  Also, only the FREE space of the disk is used, not the entire disk.

Does anyone have a clue what I am doing wrong? Thanks a lot in advance.

Cheers, 
Konstantin

---

