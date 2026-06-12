---
title: "Installation failed due to mount point is not assigned"
date: 2017-06-01
forum: Installation &amp; Upgrades
---

### Post by yotu-tuy on 2017-06-01
Hello, I'm trying to install ubuntu server with a preseed file, using RAID. This is the relevant part of my seed:
```
d-i partman-auto/expert_recipe string \
      multiraid ::                                           \
              1 1 1 free                                     \
                       $gptonly{ }                           \
                       $primary{ }                           \
                       $bios_boot{ }                         \
                       method{ biosgrub }                    \
              .                                              \
              30700 50 30732 raid                            \
                       $primary{ }                           \
                       $bootable{ }                          \
                       method{ raid }                        \
                       format{ }                             \
                       use_filesystem{ }                     \
                       filesystem{ ext4 }                    \
              .                                              \
              500 10000 1000000000 raid                      \
                       method{ raid }                        \
                       format{ }                             \
                       use_filesystem{ }                     \
                       filesystem{ ext4 }                    \
             .                                               \
              24550 512 24600 raid                           \
                       method{ raid }                        \
                       format{ }                             \
              .

d-i partman-auto-raid/recipe string \
    0 2 0 ext4 /                    \
          /dev/sda2#/dev/sdb2       \
    .                               \
    0 2 0 ext4 /data                \
          /dev/sda3#/dev/sdb3       \
    .                               \
    0 2 0 swap -                    \
          /dev/sda4#/dev/sdb4       \
    .
```I tried formatting the partitions, re-installing, re-creating the iso.... :/ I don't see anything wrong in the preseed, but yet the mount points for ext4 (sda2#sd2 and sda3#sdb3) are not being recognized.
Any help would be appreciated. 
PD I have also posted a question [here]("https://askubuntu.com/questions/920654/no-mount-point-is-assigned-for-the-ext4-file-system-in-partition-2-of-scsi5-0") which contains more detail explanation of what happened.

---

