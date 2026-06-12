---
title: "32-bit Xenial PXEboot install w/ preseed.cfg ignores expert_recipe string"
date: 2016-05-10
forum: Installation &amp; Upgrades
---

### Post by swajime on 2016-05-10
I'm trying to create 3 ext4 partitions, and no swap partition.  I am expecting the partitions to be /dev/mmcblk0p1, /dev/mmcblk0p2, and /dev/mmcblk0p3.

I have this in preseed.cfg:
```

# Alternatively, you may specify a disk to partition. If the system has only
# one disk the installer will default to using that, but otherwise the device
# name must be given in traditional, non-devfs format (so e.g. /dev/sda
# and not e.g. /dev/discs/disc0/disc).
# For example, to use the first SCSI/SATA hard disk:
#d-i partman-auto/disk string /dev/sda
d-i partman-auto/disk string /dev/mmcblk0

# In addition, you'll need to specify the method to use.
# The presently available methods are:
# - regular: use the usual partition types for your architecture
# - lvm:     use LVM to partition the disk
# - crypto:  use LVM within an encrypted partition
d-i partman-auto/method string regular

d-i partman-auto/expert_recipe string                      \
    root ::                                                \
        12800 100 12800 ext4                               \
            $primary{ } $bootable{ } method{ format }      \
            format{ } use_filesystem{ } filesystem{ ext4 } \
            mountpoint{ / }                                \
        .                                                  \
        12800 100 12800 ext4                               \
            $primary{ } $bootable{ } method {format}       \
            format{ } use_filesystem{ } filesystem{ ext4 } \
            mountpoint{ /alt-root }                        \
        .                                                  \
        6452 100 6452 ext4                                 \
            $primary{ } method {format} format{ }          \
            use_filesystem{ } filesystem{ ext4 }           \
            mountpoint{ /repo }                            \
        .

d-i partman-auto/choose_recipe select root

partman-basicfilesystems        partman-basicfilesystems/no_swap        boolean false

# This makes partman automatically partition without confirmation, provided
# that you told it what to do using one of the methods above.
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true

## Controlling how partitions are mounted
# The default is to mount by UUID, but you can also choose "traditional" to
# use traditional device names, or "label" to try filesystem labels before
# falling back to UUIDs.
d-i partman/mount_style select traditional

grub-installer  grub-installer/force-efi-extra-removable        boolean false

```

However, when the new system is up and running, fdisk -l shows me this:
```
Device         Boot    Start      End  Sectors  Size Id Type
/dev/mmcblk0p1 *        2048 53219327 53217280 25.4G 83 Linux
/dev/mmcblk0p2      53221374 61077503  7856130  3.8G  5 Extended
/dev/mmcblk0p5      53221376 61077503  7856128  3.8G 82 Linux swap / Solaris
```

I don't see what is wrong with what I've done in preseed.cfg.

Any help will be appreciated.

Thanks,


John

---

### Post by swajime on 2016-05-11
I tried again, this time using Trusty and setting no_swap to true.

Same results, still not getting what I'm asking for:

```
root@acmu:~# fdisk -l
Disk /dev/mmcblk0: 31.3 GB, 31272730624 bytes
255 heads, 63 sectors/track, 3802 cylinders, total 61079552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00009cb0

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *        2048    53219327    26608640   83  Linux
/dev/mmcblk0p2        53221374    61077503     3928065    5  Extended
/dev/mmcblk0p5        53221376    61077503     3928064   82  Linux swap / Solaris
```

---

### Post by swajime on 2016-05-11
Found an issue with the spacing and corrected that.  To no avail.
Here is the syslog:

```
May 11 19:44:36 frontend: --> SET partman-auto/method regular
May 11 19:44:36 frontend: <-- 10 partman-auto/method doesn't exist
May 11 19:44:36 frontend: --> REGISTER debian-installer/dummy partman-auto/method
May 11 19:44:36 frontend: <-- 0
May 11 19:44:36 frontend: --> SET partman-auto/method regular
May 11 19:44:36 frontend: <-- 0 value set
May 11 19:44:36 frontend: --> SUBST partman-auto/method ID partman-auto/method
May 11 19:44:36 frontend: Adding [ID] -> [partman-auto/method]
May 11 19:44:36 frontend: <-- 0
May 11 19:44:36 frontend: --> FSET partman-auto/method seen true
May 11 19:44:36 frontend: <-- 0 true
May 11 19:44:36 frontend: --> SET partman-auto/expert_recipe root :: 12800 100 12800 ext4 $primary{ } $bootable{ } method{ format } format{ } use_filesystem{ } filesystem{ ext4 } mountpoint{ / } . 12800 100 12800 ext4 $primary{ } $bootable{ } method{ format } format{ } use_filesystem{ } filesystem{ ext4 } mountpoint{ /alt-root } . 6452 100 6452 ext4 $primary{ } method{ format } format{ } use_filesystem{ } filesystem{ ext4 } mountpoint{ /repo } .
May 11 19:44:36 frontend: <-- 10 partman-auto/expert_recipe doesn't exist
May 11 19:44:36 frontend: --> REGISTER debian-installer/dummy partman-auto/expert_recipe
May 11 19:44:36 frontend: <-- 0
May 11 19:44:36 frontend: --> SET partman-auto/expert_recipe root :: 12800 100 12800 ext4 $primary{ } $bootable{ } method{ format } format{ } use_filesystem{ } filesystem{ ext4 } mountpoint{ / } . 12800 100 12800 ext4 $primary{ } $bootable{ } method{ format } format{ } use_filesystem{ } filesystem{ ext4 } mountpoint{ /alt-root } . 6452 100 6452 ext4 $primary{ } method{ format } format{ } use_filesystem{ } filesystem{ ext4 } mountpoint{ /repo } .
May 11 19:44:36 frontend: <-- 0 value set
May 11 19:44:36 frontend: --> SUBST partman-auto/expert_recipe ID partman-auto/expert_recipe
May 11 19:44:36 frontend: Adding [ID] -> [partman-auto/expert_recipe]
May 11 19:44:36 frontend: <-- 0
May 11 19:44:36 frontend: --> FSET partman-auto/expert_recipe seen true
May 11 19:44:36 frontend: <-- 0 true
May 11 19:44:36 frontend: --> SET partman-auto/choose_recipe root
May 11 19:44:36 frontend: <-- 10 partman-auto/choose_recipe doesn't exist
May 11 19:44:36 frontend: --> REGISTER debian-installer/dummy partman-auto/choose_recipe
May 11 19:44:36 frontend: <-- 0
May 11 19:44:36 frontend: --> SET partman-auto/choose_recipe root
May 11 19:44:36 frontend: <-- 0 value set
May 11 19:44:36 frontend: --> SUBST partman-auto/choose_recipe ID partman-auto/choose_recipe
May 11 19:44:36 frontend: Adding [ID] -> [partman-auto/choose_recipe]
May 11 19:44:36 frontend: <-- 0
May 11 19:44:36 frontend: --> FSET partman-auto/choose_recipe seen true
May 11 19:44:36 frontend: <-- 0 true
May 11 19:44:36 frontend: --> SET partman-basicfilesystems/no_swap true
May 11 19:44:36 frontend: <-- 10 partman-basicfilesystems/no_swap doesn't exist
May 11 19:44:36 frontend: --> REGISTER debian-installer/dummy partman-basicfilesystems/no_swap
May 11 19:44:36 frontend: <-- 0
May 11 19:44:36 frontend: --> SET partman-basicfilesystems/no_swap true
May 11 19:44:36 frontend: <-- 0 value set
May 11 19:44:36 frontend: --> SUBST partman-basicfilesystems/no_swap ID partman-basicfilesystems/no_swap
May 11 19:44:36 frontend: Adding [ID] -> [partman-basicfilesystems/no_swap]
May 11 19:44:36 frontend: <-- 0
May 11 19:44:36 frontend: --> FSET partman-basicfilesystems/no_swap seen true
May 11 19:44:36 frontend: <-- 0 true
May 11 19:44:36 frontend: --> SET partman-partitioning/confirm_write_new_label true
May 11 19:44:36 frontend: <-- 10 partman-partitioning/confirm_write_new_label doesn't exist
May 11 19:44:36 frontend: --> REGISTER debian-installer/dummy partman-partitioning/confirm_write_new_label
May 11 19:44:36 frontend: <-- 0
May 11 19:44:36 frontend: --> SET partman-partitioning/confirm_write_new_label true
May 11 19:44:36 frontend: <-- 0 value set
May 11 19:44:36 frontend: --> SUBST partman-partitioning/confirm_write_new_label ID partman-partitioning/confirm_write_new_label
May 11 19:44:36 frontend: Adding [ID] -> [partman-partitioning/confirm_write_new_label]
May 11 19:44:36 frontend: <-- 0
May 11 19:44:36 frontend: --> FSET partman-partitioning/confirm_write_new_label seen true
May 11 19:44:36 frontend: <-- 0 true
May 11 19:44:36 frontend: --> SET partman/choose_partition finish
May 11 19:44:36 frontend: <-- 10 partman/choose_partition doesn't exist
May 11 19:44:36 frontend: --> REGISTER debian-installer/dummy partman/choose_partition
May 11 19:44:36 frontend: <-- 0
May 11 19:44:36 frontend: --> SET partman/choose_partition finish
May 11 19:44:36 frontend: <-- 0 value set
May 11 19:44:36 frontend: --> SUBST partman/choose_partition ID partman/choose_partition
May 11 19:44:36 frontend: Adding [ID] -> [partman/choose_partition]
May 11 19:44:36 frontend: <-- 0
May 11 19:44:36 frontend: --> FSET partman/choose_partition seen true
May 11 19:44:36 frontend: <-- 0 true
May 11 19:44:36 frontend: --> SET partman/confirm true
May 11 19:44:36 frontend: <-- 10 partman/confirm doesn't exist
May 11 19:44:36 frontend: --> REGISTER debian-installer/dummy partman/confirm
May 11 19:44:36 frontend: <-- 0
May 11 19:44:36 frontend: --> SET partman/confirm true
May 11 19:44:36 frontend: <-- 0 value set
May 11 19:44:36 frontend: --> SUBST partman/confirm ID partman/confirm
May 11 19:44:36 frontend: Adding [ID] -> [partman/confirm]
May 11 19:44:36 frontend: <-- 0
May 11 19:44:36 frontend: --> FSET partman/confirm seen true
May 11 19:44:36 frontend: <-- 0 true
May 11 19:44:36 frontend: --> SET partman/confirm_nooverwrite true
May 11 19:44:36 frontend: <-- 10 partman/confirm_nooverwrite doesn't exist
May 11 19:44:36 frontend: --> REGISTER debian-installer/dummy partman/confirm_nooverwrite
May 11 19:44:36 frontend: <-- 0
May 11 19:44:36 frontend: --> SET partman/confirm_nooverwrite true
May 11 19:44:36 frontend: <-- 0 value set
May 11 19:44:36 frontend: --> SUBST partman/confirm_nooverwrite ID partman/confirm_nooverwrite
May 11 19:44:36 frontend: Adding [ID] -> [partman/confirm_nooverwrite]
May 11 19:44:36 frontend: <-- 0
May 11 19:44:36 frontend: --> FSET partman/confirm_nooverwrite seen true
May 11 19:44:36 frontend: <-- 0 true
May 11 19:44:36 frontend: --> SET partman/mount_style traditional
May 11 19:44:36 frontend: <-- 10 partman/mount_style doesn't exist
May 11 19:44:36 frontend: --> REGISTER debian-installer/dummy partman/mount_style
May 11 19:44:36 frontend: <-- 0
May 11 19:44:36 frontend: --> SET partman/mount_style traditional
May 11 19:44:36 frontend: <-- 0 value set
May 11 19:44:36 frontend: --> SUBST partman/mount_style ID partman/mount_style
May 11 19:44:36 frontend: Adding [ID] -> [partman/mount_style]
May 11 19:44:36 frontend: <-- 0
May 11 19:44:36 frontend: --> FSET partman/mount_style seen true
May 11 19:44:36 frontend: <-- 0 true
```

---

### Post by swajime on 2016-05-11
I tried doing just one of the partitions.  It just got stuck in a loop.  No way to copy info from syslog.  Console 4 just keeps repeating.

```
d-i partman-auto/expert_recipe string                      \
    root ::                                                \
        12800 100 12800 ext4                               \
            $primary{ } $bootable{ } method{ format }      \
            format{ } use_filesystem{ } filesystem{ ext4 } \
            mountpoint{ / }                                \
        .
```

---

### Post by swajime on 2016-05-12
I finally got this to work.  Apparently you have to give very flexible partition size parameters, and make sure the whole disk is used.

```
d-i partman-auto/expert_recipe string                      \
    root ::                                                \
        10000 10 100000 ext4                               \
            $primary{ } $bootable{ } method{ format }      \
            format{ } use_filesystem{ } filesystem{ ext4 } \
            mountpoint{ / }                                \
        .                                                  \
        10000 10 100000 ext4                               \
            $primary{ } method{ format }                   \
            format{ } use_filesystem{ } filesystem{ ext4 } \
            mountpoint{ /alt-root }                        \
        .                                                  \
        5000 20 50000 ext4                                 \
            $primary{ } method{ format } format{ }         \
            use_filesystem{ } filesystem{ ext4 }           \
            mountpoint{ /repo }                            \
        .                                                  \
        1000 30 1000000000 ext4                            \
            $primary{ } method{ format } format{ }         \
            use_filesystem{ } filesystem{ ext4 }           \
            mountpoint{ /extra }                           \
        .
```

Cheers :-)  Hopefully this will help somebody else down the line.


John

---

