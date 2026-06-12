---
title: "Raid/LVM with kickstart impossible?!"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by ionix18 on 2010-05-28
Hi guys,
I’m trying to automatically create a complex file architecture when installing Ubuntu 10.04 via netboot. I have tried with both preseed and kickstart but it seems that neither support partitioning multiple disks in an unattended fashion. This is what I’m trying to achieve:
/dev/sda should have two partitions raid.11 500MB and raid.12 with the remaining space.
/dev/sdb should have two partitions raid.21 500MB and raid.22 with the remaining space.
Then I create md0 with raid.11 and raid.21 and mount it as /boot (ext3)
I create md1 with raid.12 and raid.22 as a pv.0 volume. 
Root_vg is a volume group created on md1. On top of Root_vg, I create logical volumes: / (4G) /var (4G) and swap (4G).

What kickstart does support is a pre-script. I was wondering if I could destroy and partition the disks via some commands lines in the pre-script?
I tried doing a manual install and generating the preseed with “debconf-get-selections --installer > file” but sadly enough it did not record me clearing and creating partitions.
Any ideas on how I can achieve this? 
[http://www.centos.org/docs/4/html/rhel-sag-en-4/s1-kickstart2-options.html](http://www.centos.org/docs/4/html/rhel-sag-en-4/s1-kickstart2-options.html) describes what I am trying to achieve in section 1.4.1 but it applies to CentOS and Anaconda and does not work on Ubuntu.

Cheers,
Max

---

### Post by lemsx1 on 2010-06-07
Sure, you can do this using preseed. This is what I'm using myself:

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

Now, that used to work fine up to 9.10 or so. At 10.04 I'm getting the following issues:

1. partman/confirm boolean true is not recognize and I get ask to confirm overwriting the partition tables (I'm puzzled by this)
2. after everything installs, sometimes the second disk is not partition properly causing the whole /dev/sdb to become a RAID physical device on array md1!

These 2 are probably bugs. I have not tried opening bugs for them.

I can easily fix this manually after the installation is done (using a Live CD). However, this is not what I'm intending to do with a unattended installation!

---

### Post by edgan on 2010-06-18
I have been working on the same thing. I have gotten it to work, but only barely, and not under all circumstances.

The trick is to use "d-i partman-md/confirm_nooverwrite true", and not just once. I figured this out via "append DEBCONF_DEBUG=5", and alt-f4. Very handy in debugging preseed stuff. If I run this configuration twice, the second time it won't ask any questions. If I run it with a lvm only configuration already existing, I get questions again. I am about to start debugging it further, to see if I can find the ultimate solution.




d-i partman-auto/method string raid

d-i partman-auto/disk string /dev/sda /dev/sdb

d-i partman-auto-raid/recipe string                     \
        1 2 0 ext3 /boot                                \
                /dev/sda2#/dev/sdb2                     \
        .                                               \
        1 2 0 lvm -                                     \
                /dev/sda3#/dev/sdb3                     \
        .

# Please note that RAID partitions are tagged as "lvmignore"
# and LVM logical volumes as "defaultignore" and "lvmok".
d-i partman-auto/expert_recipe string                   \
        multiraid ::                                    \
                1 1 1 free method{ biosgrub }           \
                .                                       \
                512 512 512 raid                        \
                        $lvmignore{ }                   \
                        $primary{ }                     \
                        method{ raid }                  \
                .                                       \
                1967881 1967881 1967881 raid            \
                        $lvmignore{ }                   \
                        method{ raid }                  \
                .                                       \
                31998 31998 31998 ext4                  \
                        $defaultignore{ }               \
                        $lvmok{ }                       \
                        method{ format }                \
                        format{ }                       \
                        use_filesystem{ }               \
                        filesystem{ ext4 }              \
                        mountpoint{ / }                 \
                .                                       \
                512 512 512 linux-swap                  \
                        $defaultignore{ }               \
                        $lvmok{ }                       \
                        method{ swap }                  \
                        format{ }                       \
                .                                       \
                1935371 1935371 1935371 ext4            \
                        $defaultignore{ }               \
                        $lvmok{ }                       \
                        lv_name{ data }                 \
                .                                       \

#order matters for this block!!
d-i partman-md/confirm_nooverwrite true
d-i partman-md/device_remove_md boolean true
d-i partman-lvm/device_remove_lvm boolean true
#duplicated on purpose!!
d-i partman-md/confirm_nooverwrite true
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition \
       select Finish partitioning and write changes to disk
d-i partman/confirm boolean true
d-i mdadm/boot_degraded boolean true

---

### Post by edgan on 2010-06-20
I found one way to solve this mess. Funny enough it is a few years old.

My version is more advanced in that it does raid too.

I recommend looking into FAI. It is my next thing to investigate. The debian installer preseed method has left a very bad taste in my mouth.


Original blog post:
[http://blog.loftninjas.org/2007/07/04/complex-lvm-on-an-alternative-install-of-ubuntu-debian-installer/](http://blog.loftninjas.org/2007/07/04/complex-lvm-on-an-alternative-install-of-ubuntu-debian-installer/)

Original script formatted:
[http://proton.cygnusx-1.org/~edgan/partman_to_hell.txt](http://proton.cygnusx-1.org/~edgan/partman_to_hell.txt)

Important preseed entry:
d-i     preseed/early_command    string cd /tmp; wget [http://proton.cygnusx-1.org/~edgan/early_command;](http://proton.cygnusx-1.org/~edgan/early_command;) chmod 755 early_command ;  echo /tmp/early_command installer >> /var/lib/dpkg/info/download-installer.postinst

My version:
[http://proton.cygnusx-1.org/~edgan/early_command](http://proton.cygnusx-1.org/~edgan/early_command)

Tarball of parted, partprobe, libraries from Lucid that my version depends on:
[http://proton.cygnusx-1.org/~edgan/setup.tar](http://proton.cygnusx-1.org/~edgan/setup.tar)

---

