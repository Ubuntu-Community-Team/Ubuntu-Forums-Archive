---
title: "Preseed partitioning problem on 12.04"
date: 2013-02-01
forum: Installation &amp; Upgrades
---

### Post by xzased on 2013-02-01
Hi all, I am having trouble partitioning a server using preseed. I have 2 disks /dev/sda and /dev/sdb, I want to erase /dev/sdb and partition /dev/sda. Here is my preseed config:

```
d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string lvm
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-md/device_remove_md boolean true
d-i partman-auto/purge_lvm_from_device boolean true
d-i partman-auto-lvm/new_vg_name string vg00
d-i partman-auto-lvm/new_vg_name_exists string
d-i partman-lvm/vgcreate string vg00
d-i partman-lvm/confirm boolean true
d-i partman-auto-lvm/guided_size string max
d-i partman-auto/choose_recipe select multi
d-i partman/default_filesystem string ext4
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true
d-i partman/mount_style select traditional
```

Yet, it keeps installing on /dev/sdb and leaves /dev/sda untouched. Can anyone help me with this?

---

