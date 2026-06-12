---
title: "preseed help.  swap partitions way too big"
date: 2017-01-06
forum: Installation &amp; Upgrades
---

### Post by jdh239 on 2017-01-06
I have 2 - 500 GB drives.
[B]
What I want:[/B]
I wish to have 1 swap partition on each drive no larger than 12 GB (please don't ask me why so large).... so a total of 24 GB of swap space
I wish to have the remaining space put under a RAID1 setup for the root partition.

**What I currently have:**
My following configuration gives me a / partition of about 218 GB (in a RAID1 setup as desired), and two swap partitions that take up the remaining space.  I don't know where I have misconfigured it.  Please help.

myserver:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev             48G  4.0K   48G   1% /dev
tmpfs           9.5G  784K  9.5G   1% /run
**/dev/md0        218G  1.9G  205G   1% /**
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M     0  5.0M   0% /run/lock
none             48G     0   48G   0% /run/shm
none            100M     0  100M   0% /run/user

myuser@myserver:~$ swapon -s
Filename                                Type            Size    Used    Priority
[B]/dev/sda2                               partition       256940028       0       -1
/dev/sdb2                               partition       256940028       0       -2
[/B]
myuser@myserver:~$ free -h
             total       used       free     shared    buffers     cached
Mem:           94G       1.5G        92G       792K        18M       599M
-/+ buffers/cache:       908M        93G
**Swap:         490G         0B       490G**


#===========================================================================================
# PARTMAN PARTITIONING SECTION START
#===========================================================================================

d-i partman-md/confirm_nochanges boolean true
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-md/device_remove_md boolean true
d-i partman-lvm/confirm boolean true

d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true
d-i partman-md/confirm boolean true
d-i partman-md/confirm_nooverwrite boolean true
d-i partman-basicfilesystems/no_mount_point yes
d-i partman-basicmethods/method_only boolean false

[B]d-i partman-auto/method string raid
d-i partman-auto/disk string /dev/sda /dev/sdb

# <raidtype> <devcount> <sparecount> <fstype> <mountpoint> <devices> <sparedevices>

d-i partman-auto/expert_recipe string \
      root-swap ::                                                      \
              237000 237000 -1 raid                                     \
                      $primary{ } $bootable{ } method{ raid } format{ } \
              .                                                         \
              1024 6114 25% linux-swap                                \
                      $primary{ } method{ swap } format{ }              \
              .[/B]

[B]d-i partman-auto-raid/recipe string                                     \
              1 2 0 ext4 /                                              \
              /dev/sda1#/dev/sdb1                                       \
              .[/B]

#===========================================================================================
# PARTMAN PARTITIONING SECTION END
#===========================================================================================

---

