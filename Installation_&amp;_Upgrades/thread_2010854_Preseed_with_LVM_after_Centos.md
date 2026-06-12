---
title: "Preseed with LVM after Centos"
date: 2012-06-26
forum: Installation &amp; Upgrades
---

### Post by raztud on 2012-06-26
Hi all,

I'm fighting with this problem for few days and I can not find a solution yet.
I install Centos (5, 6) with GPT on a VM and after that, if I want to install Ubuntu (10 or 11) through preseed file I get a partition error: "Unexpected error while creating volume group. Autopartitioning using LVM failed because an error occurred while creating the volume group. Check /var/log/syslog or see virtual console 4 for details" (see 0.png)

For syslog content see attachment 1.png. 

The partitioning part of the preseed file is this:
```

####################################################################
# Disk Partitioning/Boot loader
####################################################################
# Fix for MS-7228 Motherboards
d-i preseed/include_command string if grep -q MS-7228 /sys/class/dmi/id/board_name ; then echo '/install/scripts/cylinderalignment.cfg' ; fi

d-i partman/early_command string pvremove -y -ff `list-devices disk | head -n1`* || true;

d-i partman-auto/method string lvm
d-i partman-auto/disk string /dev/sda

d-i partman-md/device_remove_md boolean true
d-i partman-md/confirm boolean true
d-i partman-md/confirm_nooverwrite boolean true

d-i partman/alignment string optimal
d-i partman-auto/purge_lvm_from_device boolean true
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-lvm/device_remove_lvm_span boolean true

d-i partman-lvm/confirm boolean true
d-i partman-lvm/confirm_nooverwrite boolean true

d-i partman/confirm boolean true

partman-base partman/exception_handler select Ignore
d-i partman/confirm_write_new_label boolean true
d-i partman/confirm_nooverwrite boolean true


d-i partman/choose_partition select finish
d-i partman-partitioning/confirm_write_new_label boolean true

d-i partman-auto-lvm/new_vg_name string VolGroup0

d-i partman-auto/choose_recipe select expert_recipe

d-i partman-auto/expert_recipe string brtfs :: 1 1 1 free $gptonly{ } $primary{ } $bios_boot{ } method{ biosgrub } . logical-groups :: 100 100 -1 lvm $defaultignore{ } $primary{ } method{ lvm } device { /dev/sda } vg_name{ VolGroup0 } . logical-volumes :: 100 1000 100 ext2 $primary{ } $bootable{ } method{ format } format{ } use_filesystem{ } filesystem{ ext2 } mountpoint{ /boot } . 4096 900 4096 linux-swap $defaultignore{ } $lvmok{ } in_vg{ VolGroup0 } lv_name{ lv_swap } method{ swap } format{ } label{ lv_swap } . 64 2048 2048 ext4 $defaultignore{ } $lvmok{ } in_vg{ VolGroup0 } lv_name{ lv_tmp } method{ format } format{ } use_filesystem{ } filesystem{ ext4 } mountpoint{ /tmp } label { lv_tmp } . 64 2048 16000000 ext4 $primary{ } $defaultignore{ } $lvmok{ } in_vg{ VolGroup0 } lv_name{ lv_rest } method{ format } format{ } use_filesystem{ } filesystem{ ext4 } mountpoint{ / } label { lv_rest } .

d-i grub-installer/only_debian boolean true

d-i grub-installer/with_other_os boolean true
d-i grub-installer/bootdev string /dev/sda

```


What actually it's happening, it's the fact the Centos GPT partition it's destroyed after executing that preseed and the new linux lvm partition is created BUT I still have that error (see 3.png)
If I reboot the VM, the installation will work with the same preseed file without any error. 

If I will install again Centos and try to install Ubuntu again, I will have the same error.

There is any solution to fix this error with the preseed ?

Thank you.

---

