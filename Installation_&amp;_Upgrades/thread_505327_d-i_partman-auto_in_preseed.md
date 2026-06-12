---
title: "d-i partman-auto in preseed?"
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by mackis5 on 2007-07-20
I have a almost perfect preseed environment setup, except on one topic, which is the partman-auto.
It is working (goes through the kickstart without any questions), but not as I would like though. The only setting I got to work, is the automatic settings, which creates "EXT3" file as follows:
/dev/sda1 on / type ext3

The settings I would like to pass to partman, are the following:
/dev/sda1 "/" "reiserfs" 75 Gb
/dev/sda5 "linux swap"  5 Gb 

Here are parts of my preseed.cfg file
```

d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string regular
d-i partman-auto/purge_lvm_from_device boolean true
d-i partman-lvm/confirm boolean true
d-i partman-auto/choose_recipe \ select Separate / partitions
d-i     partman/confirm_write_new_label boolean true
d-i     partman/choose_partition \ select Finish partitioning and write changes to disk
d-i     partman/confirm                 boolean true

```

---

### Post by mackis5 on 2007-07-23
bump

Must be someone who can answer my question, or at least give me a hint where to find the information or who to contact.

Thanks,

---

### Post by mackis5 on 2007-07-24
After a lot of testing this is my setup that is working, without any input from the user:

It might be useful for someone, so I cut'n paste the code here.

> 
# If one of the disks that are going to be automatically partitioned
# contains an old LVM configuration, the user will normally receive a
# warning. This can be preseeded away...
d-i partman-auto/purge_lvm_from_device boolean true
# And the same goes for the confirmation to write the lvm partitions.
d-i partman-lvm/confirm boolean true
# Create a small /boot partition, suitable swap, and uses the rest of the space
# The next row HAS TO BE IN ONE ROW!!!!! It will create a small "/boot", a swap, and a "/" for the system
d-i partman-auto/expert_recipe string boot-root :: 100 50 100 reiserfs $primary{ } $bootable{ } method{ regular } format{ } use_filesystem{ } filesystem{ reiserfs } mountpoint{ /boot } . 500 10000 1000000000 reiserfs method{ regular } format{ } use_filesystem{ } filesystem{ reiserfs } mountpoint{ / } . 64 512 2048 linux-swap method{ swap } format{ } .
d-i     partman/choose_partition select Finish partitioning and write changes to disk
d-i     partman/confirm                 boolean true


---

