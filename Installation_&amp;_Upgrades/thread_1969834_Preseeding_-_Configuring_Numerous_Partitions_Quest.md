---
title: "Preseeding - Configuring Numerous Partitions Question"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by Sniperm4n on 2012-04-30
Hi all,

I'm attempting to create my first Ubuntu Server 10.04-4 LTS x64 preseed file and I'm afraid I can't figure out the hard drive partitioning aspect:

I have a 2TB hard disk that I need configured as follows (please note this system has hardware RAID that is already configured, so the OS install should merely see one large hard drive):

Partitions:
/ - 40 GB (ext4, must be bootable)
/swap - 32 GB
/local - all remaining free space (ext4)

The file systems need to be ext4 (with the exception of swap of course), and / must be bootable. I also need to use regular partitions rather than LVM. Also, I don't care about any data that's currently on the disk. I've been trying to cook something up via the examples on this page to no avail:

[http://www.tylerlesmann.com/2008/jul/06/fun-preseed/](http://www.tylerlesmann.com/2008/jul/06/fun-preseed/)

Any help is greatly appreciated (please note I'm incredibly new to *nix, so please handle with care)! =)

Thanks,
-Snipe

*EDIT* I just found this example, but am uncertain how to modify it based on my exact needs:
# If not, you can put an entire recipe into the preconfiguration file in one # (logical) line. This example creates a small /boot partition, suitable # swap, and uses the rest of the space for the root partition: #d-i partman-auto/expert_recipe string                         \ #      boot-root ::                                            \ #              40 50 100 ext3                                  \ #                      $primary{ } $bootable{ }                \ #                      method{ format } format{ }              \ #                      use_filesystem{ } filesystem{ ext3 }    \ #                      mountpoint{ /boot }                     \ #              .                                               \ #              500 10000 1000000000 ext3                       \ #                      method{ format } format{ }              \ #                      use_filesystem{ } filesystem{ ext3 }    \ #                      mountpoint{ / }                         \ #              .                                               \ #              64 512 300% linux-swap                          \ #                      method{ swap } format{ }                \ #              .

---

### Post by oldfred on 2012-05-01
I know nothing about preseeding & RAID, but if drive is 2TB are you booting with UEFI or BIOS. Is drive formated to gpt or MBR in the RAID?

Ubuntu defaults to gpt for drives over 1TB, but you can use MBR up to 2TB. If you have formated in advance inside you RAID it should not matter unless you are booting with UEFI.

---

### Post by Sniperm4n on 2012-05-01
Hi oldfred,

The drive has already been formatted within the RAID BIOS, and appears as one large drive to the Ubuntu installer. I'm still stuck on the partitioning aspect of the preseed process =(.

Thanks,
-Snipe

> **oldfred said:**
> I know nothing about preseeding & RAID, but if drive is 2TB are you booting with UEFI or BIOS. Is drive formated to gpt or MBR in the RAID?

Ubuntu defaults to gpt for drives over 1TB, but you can use MBR up to 2TB. If you have formated in advance inside you RAID it should not matter unless you are booting with UEFI.

---

### Post by Sniperm4n on 2012-05-03
TobiSGD over at LinuxQuestions.org was able to resolve this for me. Here's the solution:

"At first, if you set *d-i partman-auto/choose_recipe select atomic* the installer will not use your recipe, so comment that out.

Here's your actual recipe, corrected with the sizes you want:

d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string regular
d-i partman-lvm/purge_lvm_from_device boolean true
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-md/device_remove_md boolean true
d-i partman-lvm/confirm boolean true
#d-i partman-auto/choose_recipe select atomic
d-i partman-auto/expert_recipe string                         \
boot-root :: \ 40000 50 41000 ext4 \ $primary{ } $bootable{ } \ method{ format } format{ } \ use_filesystem{ } filesystem{ ext4 } \ mountpoint{ / } \ . \ 500 10000 1000000000 ext4 \ method{ format } format{ } \ use_filesystem{ } filesystem{ ext4 } \ mountpoint{ /local } \ . \ 32000 512 33000 linux-swap \ method{ swap } format{ } \ .

d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true

I have changed the mount-points and the sizes for the partitions. Note that it is not possible to give exact sizes to the installer with preseeding, so your /-partition is set to be anywhere between 40000MB and 41000MB and your swap will be anywhere between 32000MB and 33000MB. The rest of the disk will be partitioned and mounted as /local."

---

