---
title: "Preseed: LVM / MDRAID / GPT problems"
date: 2016-10-24
forum: Installation &amp; Upgrades
---

### Post by boxrick on 2016-10-24
Good afternoon, I am currently using Ubuntu 16 Xenial and trying to get a preseed file working for setting up partitioning.
 
I have spent a considerable amount of time on this and am rather close. Simply put I require a RAID 1 partition, with LVM living on top and using the GPT labels. I mostly have this working however I am getting errors when GRUB2 tries to install at the end. 

Perhaps someone could point out a way I can fix this configuration:

> # GPT Optionsd-i partman-basicfilesystems/choose_label                string gpt
d-i partman-basicfilesystems/default_label               string gpt
d-i partman-partitioning/choose_label                    string gpt
d-i partman-partitioning/default_label                   string gpt
d-i partman/choose_label                                 string gpt
d-i partman/default_label                                string gpt
partman-partitioning partman-partitioning/choose_label   select gpt


# LVM Options
d-i     partman-auto/purge_lvm_from_device               boolean true
d-i     partman-auto-lvm/new_vg_name                     string volgroup0
d-i     partman-auto-lvm/guided_size                     string 100%


# Set up Raid 1 - MDRAID
d-i   partman-auto/method                                string raid
d-i   partman-auto/disk                                  string /dev/sda /dev/sdb
partman-auto/choose_recipe                               select multiraid
d-i   partman-auto/alignment                             string optimal


# Set up partitioning, first two are for MDRAID then we build LVM partitions on top of this
# <raidtype> <devcount> <sparecount> <fstype> <mountpoint> <devices> <sparedevices>
d-i partman-auto-raid/recipe string                            \
  1 2 0 ext4 /boot raidid=1 .                                  \
  1 2 0 lvm  -     raidid=2 .


d-i partman-auto/expert_recipe string                          \
      multiraid ::                                             \
        1024 1024 1024 raid                                    \
          $gptonly{ }                                          \
          $primary{ }                                          \
          $lvmignore{ }                                        \
          $bootable{ }                                         \
          $bios_boot{ }                                        \
          method{ raid }                                       \
          raidid{ 1 }                                          \
        .                                                      \
        2048 10000 -1 raid                                     \
          $gptonly{ }                                          \
          $primary{ }                                          \
          $lvmignore{ }                                        \
          method{ raid }                                       \
          raidid{ 2 }                                          \
        .                                                      \
        4096 100 4096 ext4                                     \
          $gptonly{ }                                          \
          $defaultignore $lvmok{ } lv_name{ root }             \
          method{ format } format{ }                           \
          use_filesystem{ } filesystem{ ext4 }                 \
          mountpoint{ / }                                      \
        .                                                      \
        8192 100 4096 linux-swap                               \
          $gptonly{ }                                          \
          $defaultignore $lvmok{ } lv_name{ swap }             \
          method{ swap } format{ }                             \
        .                                                      \
        256 10000 -1 ext4                                      \
          $gptonly{ }                                          \
          $defaultignore $lvmok{ } lv_name{ split }            \
          method{ lvm }                                        \
        .
        
d-i     partman-partitioning/confirm_write_new_label  boolean true
d-i     partman/confirm                               boolean true
d-i     partman/confirm_nooverwrite                   boolean true
d-i     partman/confirm_write_new_label               boolean true
d-i     partman/choose_partition                      select finish
d-i     partman-md/confirm_nooverwrite                boolean true
d-i     partman-md/device_remove_md                   boolean true
d-i     partman-md/confirm                            boolean true
d-i     partman-lvm/confirm_nooverwrite               boolean true
d-i     partman-lvm/device_remove_lvm                 boolean true
d-i     partman-lvm/confirm                           boolean true
d-i     mdadm/boot_degraded                           boolean true




---

### Post by boxrick on 2016-10-24
Managed to fix this with a simple change to biosgrub, putting full fixed version here for future reference and searches. I couldn't find any examples anywhere of all this working alongside each other. 

> # GPT Optionsd-i partman-basicfilesystems/choose_label                string gpt
d-i partman-basicfilesystems/default_label               string gpt
d-i partman-partitioning/choose_label                    string gpt
d-i partman-partitioning/default_label                   string gpt
d-i partman/choose_label                                 string gpt
d-i partman/default_label                                string gpt
partman-partitioning partman-partitioning/choose_label   select gpt


# LVM Options
d-i     partman-auto/purge_lvm_from_device               boolean true
d-i     partman-auto-lvm/new_vg_name                     string volgroup0
d-i     partman-auto-lvm/guided_size                     string 100%


# Set up Raid 1 - MDRAID
d-i   partman-auto/method                                string raid
d-i   partman-auto/disk                                  string /dev/sda /dev/sdb
partman-auto/choose_recipe                               select multiraid
d-i   partman-auto/alignment                             string optimal


# Set up partitioning, first two are for MDRAID then we build LVM partitions on top of this
# <raidtype> <devcount> <sparecount> <fstype> <mountpoint> <devices> <sparedevices>
d-i partman-auto-raid/recipe string                            \
  1 2 0 ext4 /boot raidid=1 .                                  \
  1 2 0 lvm  -     raidid=2 .


d-i partman-auto/expert_recipe string                          \
      multiraid ::                                             \
        1024 1024 1024 raid                                    \
          $gptonly{ }                                          \
          $primary{ }                                          \
          $lvmignore{ }                                        \
          $bootable{ }                                         \
          $bios_boot{ }                                        \
          method{ biosgrub }                                   \
          raidid{ 1 }                                          \
        .                                                      \
        2048 10000 -1 raid                                     \
          $gptonly{ }                                          \
          $primary{ }                                          \
          $lvmignore{ }                                        \
          method{ raid }                                       \
          raidid{ 2 }                                          \
        .                                                      \
        4096 100 4096 ext4                                     \
          $gptonly{ }                                          \
          $defaultignore $lvmok{ } lv_name{ root }             \
          method{ format } format{ }                           \
          use_filesystem{ } filesystem{ ext4 }                 \
          mountpoint{ / }                                      \
        .                                                      \
        8192 100 4096 linux-swap                               \
          $gptonly{ }                                          \
          $defaultignore $lvmok{ } lv_name{ swap }             \
          method{ swap } format{ }                             \
        .                                                      \
        256 10000 -1 ext4                                      \
          $gptonly{ }                                          \
          $defaultignore $lvmok{ } lv_name{ split }            \
          method{ lvm }                                        \
        .


d-i     partman-partitioning/confirm_write_new_label  boolean true
d-i     partman/confirm                               boolean true
d-i     partman/confirm_nooverwrite                   boolean true
d-i     partman/confirm_write_new_label               boolean true
d-i     partman/choose_partition                      select finish
d-i     partman-md/confirm_nooverwrite                boolean true
d-i     partman-md/device_remove_md                   boolean true
d-i     partman-md/confirm                            boolean true
d-i     partman-lvm/confirm_nooverwrite               boolean true
d-i     partman-lvm/device_remove_lvm                 boolean true
d-i     partman-lvm/confirm                           boolean true
d-i     mdadm/boot_degraded                           boolean true




---

