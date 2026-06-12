---
title: "Help (or resources) for preseeding Ubuntu installation"
date: 2014-05-13
forum: Installation &amp; Upgrades
---

### Post by timfenney on 2014-05-13
Hello,

I'm trying to preseed an installation of Ubuntu 14.04 Server. I don't want to use Kickstart (unless I have to).

Right now I am having problems with preseeding the partitioning step, and the installer fails with "no root partition found." Before I ask more specific questions about specific errors, can someone help me find better documentation?

At the moment, I'm trying to find out with the all the numeric constants mean in the following snippet:
```
# If not, you can put an entire recipe into the preconfiguration file in one
# (logical) line. This example creates a small /boot partition, suitable
# swap, and uses the rest of the space for the root partition:
#d-i partman-auto/expert_recipe string                         \
#      boot-root ::                                            \
#              40 50 100 ext3                                  \
#                      $primary{ } $bootable{ }                \
#                      method{ format } format{ }              \
#                      use_filesystem{ } filesystem{ ext3 }    \
#                      mountpoint{ /boot }                     \
#              .                                               \
#              500 10000 1000000000 ext3                       \
#                      method{ format } format{ }              \
#                      use_filesystem{ } filesystem{ ext3 }    \
#                      mountpoint{ / }                         \
#              .                                               \
#              64 512 300% linux-swap                          \
#                      method{ swap } format{ }                \
#              .
```

I think the only thing I have left to figure out is how to preseed the installer so that it can replicate my desired partitioning scheme. Right now I have a software raid 0 set on two drives, **/dev/sda** and **/dev/sdb**. It is a UEFI boot situation (on a Gigabyte Haswell board), so I think I need an EFI partition (of 512 MB or so), followed by a physical partition for the raid, on each of the two disks.

Finally, I construct the raid from the two partitions, and format that ext4 and use as /.

I don't mind if I have to fart around a little more, but can someone please point me in the right direction?

Tim

---

### Post by TheFu on 2014-05-13
Don't really know what you mean by pre-seeding, but cobbler does installations from PXE.

---

