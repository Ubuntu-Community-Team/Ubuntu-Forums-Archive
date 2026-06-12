---
title: "Partitioning with preseeding method"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by Markuss90 on 2007-11-22
Hello,

My preseed file works fine, except the partitioning.
> 
d-i partman-auto/disk string /dev/discs/disc0/disc
d-i partman-auto/method string lvm
d-i partman-auto/purge_lvm_from_device boolean true
d-i partman-lvm/confirm boolean true
d-i partman-auto/init_automatically_partition \
        select Guided - use entire disk and set up LVM

d-i partman-auto/expert_recipe string                         \
      boot-root ::                                                        \
              200 200 200 ext3                                       \
                      $primary{ } $bootable{ }                   \
                      method{ format } format{ }               \
                      use_filesystem{ } filesystem{ ext3 }   \
                      mountpoint{ /boot }                           \
                                                                              \
              1 1073741824 1073741824 ext3                  \
                      method{ format } format{ } $lvmok{ }\
                      use_filesystem{ } filesystem{ ext3 }   \
                      mountpoint{ /home }                          \
                                                                               \
              7000 7000 7000 ext3                                   \
                      method{ format } format{ } $lvmok{ }\
                      use_filesystem{ } filesystem{ ext3 }   \
                      mountpoint{ / }                                  \
              .                                                               \
              2048 2048 2048 swap                                \
                      method{ swap } format{ }                 \


d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition \
        select Finish partitioning and write changes to disk
d-i partman/confirm boolean true


it isnt using the lvm...
can anyone tell me why?

tia

---

