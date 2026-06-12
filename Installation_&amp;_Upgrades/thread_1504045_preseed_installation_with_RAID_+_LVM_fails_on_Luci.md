---
title: "preseed installation with RAID + LVM fails on Lucid 10.04"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by lemsx1 on 2010-06-07
(Update: created a bug in Launchpad as nobody seems to have an answer to this. [https://bugs.launchpad.net/ubuntu/+source/partman-auto-raid/+bug/591909](https://bugs.launchpad.net/ubuntu/+source/partman-auto-raid/+bug/591909) )
(Update2: there is now a work around for this problem. see last comment or launchpad bug from the previous URL)

I'm getting the following issues when preseeding a system with 2 (exact same disks) as mirrors with LVM:

1. "d-i partman/confirm boolean true" is not recognize and I get asked to confirm overwriting the partition tables (I'm puzzled by this)

2. after everything installs, the system reboots and the second disk is added to /dev/md1 as a RAID physical device! This destroys everything and initramfs displays error

These 2 are probably bugs. I have not tried opening bugs for them.

I can easily fix this manually after the installation is done (using a Live CD). However, this is not what I'm intending to do with a unattended installation!

This is the relevant information from the preseed file I'm using:

### Partitioning
# 2009-10-20 14:30 EDT 
d-i     partman-auto/method             string raid

# If one of the disks that are going to be automatically partitioned
# contains an old LVM configuration, the user will normally receive a
# warning. This can be preseeded away...
# This makes partman automatically partition without confirmation.

# Write the changes to the storage devices and configure RAID?
d-i     partman-md/confirm              boolean true

# Write a new empty partition table?
#d-i partman-partitioning/confirm_write_new_label boolean true
d-i     partman/confirm_write_new_label boolean true

# Remove existing software RAID partitions?
d-i     partman-md/device_remove_md     boolean true

# Write the changes to disks and configure LVM?
d-i     partman-lvm/confirm             boolean true

d-i     partman/choose_partition        select finish
d-i     partman/confirm_nooverwrite     boolean true

# Write the changes to disks?
d-i     partman/confirm                 boolean true

d-i     partman-auto/disk               string /dev/sda /dev/sdb

d-i partman-lvm/device_remove_lvm   boolean true
d-i partman-lvm/device_remove_lvm_span boolean true

d-i partman-auto-lvm/new_vg_name    string bootdisk

d-i partman-auto-lvm/guided_size    string max

# Notes:
#  - partitions are created in the order they are defined
#  - higher priority takes precendence
#  - highest priority number chosen is 5,000
#  - very impotant!! do not leave spaces after \ or it won't work
#  RAID:
# /dev/md0 -> /boot         -> 100M - 256MB (high priority)
# /dev/md1 -> LVM VG bootdisk  -> 500M  - 1T (high priority)
# LVM:
# /dev/mapper/bootdisk-root   -> /     -> 5G - 1T (high priority)
# /dev/mapper/bootdisk-swap_1 -> swap  -> 3G - 3 times size of RAM (high priority)
#
# Last you need to specify how the previously defined partitions will be
# used in the RAID setup. Remember to use the correct partition numbers
# for logical partitions.
# Parameters are:
# <raidtype> <devcount> <sparecount> <fstype> <mountpoint> \
#          <devices> <sparedevices>
# RAID levels 0, 1, 5, 6 and 10 are supported; devices are separated using "#"
d-i partman-auto-raid/recipe string                        \
    1 2 0 ext4 /boot                                       \
          /dev/sda1#/dev/sdb1                              \
    .                                                      \
    1 2 0 lvm /                                            \
          /dev/sda2#/dev/sdb2                              \
    .

# RAID partitions are tagged as "lvmignore"
# and LVM logical volumes as "defaultignore" and "lvmok"
d-i partman-auto/expert_recipe string                      \
      multiraid ::                                         \
              100 512 256 raid                             \
                      $lvmignore{ }                        \
                      $primary{ }                          \
                      method{ raid }                       \
              .                                            \
              900 5000 1000000000 raid                     \
                      $lvmignore{ }                        \
                      $primary{ }                          \
                      method{ raid }                       \
              .                                            \
              700 5000 1000000000 ext4                     \
                      $defaultignore{ }                    \
                      $lvmok{ }                            \
                      method{ format }                     \
                      format{ }                            \
                      use_filesystem{ }                    \
                      filesystem{ ext4 }                   \
                      options/relatime{ relatime }         \
                      mountpoint{ / }                      \
              .                                            \
              256 3000 300% linux-swap                     \
                      $defaultignore{ }                    \
                      $lvmok{ }                            \
                      method{ swap }                       \
                      format{ }                            \
              .


mdadm                   mdadm/boot_degraded                     boolean true

---

### Post by joker- on 2010-06-10
I am having the same problem. I am trying to do unattended PXE installation inside Virtualbox (one server guest, one client guest) and it asks to confirm the partition changes every time.

In first attempt, I used lvm, second attempt was with regular.

d-i partman-auto/method string lvm
d-i partman-auto/method string regular

I haven't been able to solve this yet, but my current guess is, it has something to do with partman/choose_partition. You, like I, seem to have used a value "select finish". This value is used in most of the example files also. However, if you look at [this example file]("http://www.debian-administration.org/articles/394"), it uses value "select Finish partitioning and write changes to disk"

I'm going to give it a try. Not that exact value, though. Possible alternative select values need to checked first (what are the actual button labels the installer gives you).

---

### Post by r.gelobter on 2010-07-09
The preseed line that "selects finish" needs to be in a certain order in your preseed, the example-preseed does not follow this.

# Partitioning
d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string lvm
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-md/device_remove_md boolean true
d-i partman-lvm/confirm boolean true
**d-i partman/choose_partition select finish**
d-i partman-auto-lvm/guided_size string max
# - atomic: all files in one partition
d-i partman-auto/choose_recipe select atomic
d-i partman/default_filesystem string ext3
d-i partman/confirm_write_new_label boolean true
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true

---

### Post by lemsx1 on 2010-07-20
> **r.gelobter said:**
> The preseed line that "selects finish" needs to be in a certain order in your preseed, the example-preseed does not follow this.

# Partitioning
d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string lvm
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-md/device_remove_md boolean true
d-i partman-lvm/confirm boolean true
**d-i partman/choose_partition select finish**
d-i partman-auto-lvm/guided_size string max
# - atomic: all files in one partition
d-i partman-auto/choose_recipe select atomic
d-i partman/default_filesystem string ext3
d-i partman/confirm_write_new_label boolean true
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true

If you look at the bug report ( [https://bugs.launchpad.net/ubuntu/+source/partman-auto-raid/+bug/591909](https://bugs.launchpad.net/ubuntu/+source/partman-auto-raid/+bug/591909) ), the suggestion to fix problem #1 is to simply add:

d-i partman-md/confirm_nooverwrite boolean true

Now I get no questions asked during boot (except for postfix configuration which I'll fix shortly).

After preseed is done, however, the system still boots into some weird state where /dev/sdb and /dev/sda are part of /dev/md1 instead of /dev/sda2 and /dev/sdb2 part of /dev/md1. This also gets a weird name /dev/md1p1.

/dev/sda1 and /dev/sdb1 should be in /dev/md0 (as they are during preseed'ing) but they get wiped by mdadm during sync of the above partitions and /dev/md0p0 has no actual drives attached to it.

In short, like the original post and all screwed up. At least 1 problem has been fixed. Perhaps in another 6 months I'll be able to find a solution for the other one :-(

---

### Post by lemsx1 on 2010-07-23
There is now a work around for this problem

[https://bugs.launchpad.net/ubuntu/+source/partman-auto-raid/+bug/591909/comments/8](https://bugs.launchpad.net/ubuntu/+source/partman-auto-raid/+bug/591909/comments/8)

Essentially:

1. use boot param partman/alignment=cylinder (or d-i in preseed)
2. use the following recipe

d-i partman-auto-raid/recipe string \
 1 2 0 ext4 /boot   /dev/sda1#/dev/sdb1 .  1 2 0 lvm  /       /dev/sda5#/dev/sdb5 .

# RAID partitions are tagged as "lvmignore"
# and LVM logical volumes as "defaultignore" and "lvmok"
d-i partman-auto/expert_recipe string \
    multiraid :: \
    100 512 256 raid $lvmignore{ } $primary{ } method{ raid } . \
    900 5000 1000000000 raid $lvmignore{ } method{ raid } . \
    700 5000 200000 ext4 $defaultignore{ } $lvmok{ } \
        method{ format } format{ } use_filesystem{ } filesystem{ ext4 } \
        options/relatime{ relatime } mountpoint{ / } . \
    256 3000 4500 linux-swap $defaultignore{ } $lvmok{ } method{ swap } format{ } .

---

