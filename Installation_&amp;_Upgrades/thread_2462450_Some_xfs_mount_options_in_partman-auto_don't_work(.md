---
title: "Some xfs mount options in partman-auto don't work(Ubuntu Server 20.04 LTS)"
date: 2021-05-21
forum: Installation &amp; Upgrades
---

### Post by mangobowl on 2021-05-21
I tried my preseed file and found that when pxe installing, partman-auto seems to only take effect part of the xfs mount options.

my preseed file of partitioning:

```
# Disk Partitioning
# Use Regular, and wipe out anything that already exists
d-i partman-auto/disk string /dev/sda
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true
d-i partman-auto/method string regular
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-lvm/confirm boolean true
d-i partman-lvm/confirm_nooverwrite boolean true
d-i partman-md/device_remove_md boolean true
d-i partman-partitioning/confirm_write_new_label boolean true


# You can choose one of the three predefined partitioning recipes:
# - atomic: all files in one partition
# - home:   separate /home partition
# - multi:  separate /home, /usr, /var, and /tmp partitions
d-i partman-auto/choose_recipe select atomic


# If you just want to change the default filesystem from ext3 to something
# else, you can do that without providing a full recipe.
d-i partman/default_filesystem string ext4
d-i partman-auto/expert_recipe string                         \
      boot-root ::                                            \
              128 192 256 fat32                               \
                     $iflabel{ gpt }                          \
                     method{ efi } format{ }                  \
              .                                               \
              16384 65536 -1 ext4         \
                     $primary{ } $bootable{ }                 \
                     method{ format } format{ }               \
                     use_filesystem{ } filesystem{ ext4 }     \
                     mountpoint{ / }                          \
              .                                               \
              16384 131072 -1 xfs                             \
                     method{ format } format{ }               \
                     use_filesystem{ } filesystem{ xfs }      \
                     mountpoint{ /var/lib/docker }            \
[B]                     options/pquota{ pquota }                   \
                     options/noatime{ noatime }               \[/B]
              .                                               \
              4096 4096 4096 linux-swap     \
                     method{ swap } format{ }                 \
              .
```


After the installation is complete, It was expected that the xfs partition should have 'noatime,pquota' mount options, but the mount options in the /etc/fstab file show only 'noatime', without 'pquota'.


```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=4fe2f99a-74a1-4792-a01b-2e717b8f2814 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=7941-9BD0  /boot/efi       vfat    umask=0077      0       1
# /var/lib/docker was on /dev/sda3 during installation
UUID=5c563c14-2324-4060-ba54-9596b8cfe02f /var/lib/docker xfs     noatime         0       0
# swap was on /dev/sda4 during installation

UUID=77f9f570-9d77-467f-a5a0-55e3bf7fdcc6 none            swap    sw              0       0
```


Is this a bug or is it supposed to be?

---

