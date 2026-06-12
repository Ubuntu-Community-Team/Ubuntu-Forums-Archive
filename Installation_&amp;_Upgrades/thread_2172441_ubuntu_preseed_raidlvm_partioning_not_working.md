---
title: "ubuntu preseed raid/lvm partioning not working"
date: 2013-09-05
forum: Installation &amp; Upgrades
---

### Post by grosse2 on 2013-09-05
Hi,

I am trying to install a ubuntu 12.04 server with lvm on mirroring.
What I want is:

/boot  # raid mirror
/        # lvm volume on raid device
swap # lvm volume on raid device

The problem is it is choking on creating the second raid device ( md1 ).
The system log says there is not partition /dev/sda2.
I would think this setup would create a /dev/sda2 partition. 
Anyone have any ideas/suggestions?
Relevant part of pressed:

d-i partman-auto/method string raid
d-i partman/confirm_write_new_label boolean true
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-md/device_remove_md boolean true
d-i partman-lvm/confirm boolean true
d-i partman/choose_partition select finish
d-i partman/confirm_nooverwrite boolean true
d-i partman-auto/disk string /dev/sda /dev/sdb
d-i partman-auto-lvm/new_vg_name string sysvg 


d-i partman-auto/expert_recipe string \
multi-raid :: \
        1024 30 1024 raid \
        $lvmignore{ } \
        $primary{ } method{ raid } \
        . \
        400000 1020 420000 raid     \
        $lvmignore{ }               \                
        $primary{ } method{ raid }  \
        . \
        40000 1020 45000 ext4      \
        $defaultignore{ }        \
        $lvmok{ }                \
        lv_name{ root }  \
        method{ format } \
        format{ } \
        use_filesystem{ } \
        filesystem{ ext4 } \
        mountpoint{ / } \
        . \
        2048 60 2048 swap \
        $defaultignore{ } \
        $lvmok{ } \
        lv_name{ swap } \
        method{ swap } \
        format{ } \
        .

d-i partman-auto-raid/recipe string \
    1 2 0 ext2 /boot \
          /dev/sda1#/dev/sdb1 \
    . \
    1 2 0 lvm - \
          /dev/sda2#/dev/sdb2 \
    .



d-i mdadm/boot_degraded boolean false
d-i partman-md/confirm boolean true
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish 
d-i partman/confirm boolean true
d-i partman-md/confirm_nooverwrite boolean true
d-i partman/confirm_nooverwrite boolean true

---

