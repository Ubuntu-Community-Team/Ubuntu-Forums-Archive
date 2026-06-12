---
title: "Cannot auto-partition with preseed config"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by mweichert on 2007-03-26
Hello,

I have been trying desperately to get my preseed configuration to auto-partition my hard disk drive, but everything I try doesn't seem to work. 

Here is what I have currently:

> 
d-i partman-auto/disk string /dev/discs/disc0/disc
d-i partman-auto/expert_recipe string                         \
      boot-root ::                                            \
              40 50 100 ext3                                  \
                      $primary{ } $bootable{ }                \
                      method{ format } format{ }              \
                      use_filesystem{ } filesystem{ ext3 }    \
                      mountpoint{ /boot }                     \
              .                                               \
              500 10000 1000000000 ext3                       \
                      method{ format } format{ }              \
                      use_filesystem{ } filesystem{ ext3 }    \
                      mountpoint{ / }                         \
              .                                               \
              64 512 300% linux-swap                          \
                      method{ swap } format{ }                \
              .

d-i partman-auto/purge_lvm_from_device boolean true
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition \
       select Finish partitioning and write changes to disk
d-i partman/confirm boolean true


However, the doesn't work. The installer still asks me if I'd like to partition the free space or the entire disk.

Any suggestions would be greatly appreciated!

Thanks,
Mike.

---

### Post by zvacet on 2007-03-26
If you choose manualy partition I think it will ask you what do you want(create new partition or autocreate partition or something like that).

---

### Post by paul.clayton on 2007-05-04
Got the same issue. I suspect there is something fubar in the preseed process or partman itself.

From what I can see preseed is not totally automatic.

---

### Post by rizza on 2007-05-13
all you need to do is change you /dev/disc/disc0... to /dev/hda or hdb or sda or sdb depending on if your disks are ide or scsi/sata. I posted previosly on similar issue plus more. You can find that post my searching for preseed and find my user name as the poster. Good luck.

---

