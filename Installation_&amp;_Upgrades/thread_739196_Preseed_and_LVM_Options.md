---
title: "Preseed and LVM Options"
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by Scaryman on 2008-03-29
Hello,
i try to make a preseed with LVM. I found this Example

```

d-i partman-auto/disk string /dev/discs/disc0/disc
d-i partman-auto/method string lvm
d-i partman-auto/purge_lvm_from_device boolean true
d-i partman-lvm/confirm boolean true
d-i partman-auto/init_automatically_partition \
	select Guided - use entire disk and set up LVM

d-i partman-auto/expert_recipe string                         \
      boot-root ::                                            \
              40 300 300 ext3                                 \
                      $primary{ } $bootable{ }                \
                      method{ format } format{ }              \
                      use_filesystem{ } filesystem{ ext3 }    \
                      mountpoint{ /boot }                     \
              .                                               \
              500 10000 1000000000 ext3                       \
                      method{ format } format{ } $lvmok{ }    \
                      use_filesystem{ } filesystem{ ext3 }    \
                      mountpoint{ / }                         \
              .                                               \
              600000 600000 600000 ext3                       \
                      method{ format } format{ } $lvmok{ }    \
                      use_filesystem{ } filesystem{ ext3 }    \
                      mountpoint{ /opt/amanda }               \
              .                                               \
              500 9000 5000 ext3                              \
                      method{ format } format{ } $lvmok{ }    \
                      use_filesystem{ } filesystem{ ext3 }    \
                      mountpoint{ /var }                      \
              .                                               \
              500 9000 5000 ext3                              \
                      method{ format } format{ } $lvmok{ }    \
                      use_filesystem{ } filesystem{ ext3 }    \
                      mountpoint{ /tmp }                      \
              .                                               \
              64 512 200% linux-swap $lvmok{ }                \
                      method{ swap } format{ }                \
              .

d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition \
	select Finish partitioning and write changes to disk
d-i partman/confirm boolean true

```


This ends up giving me a system disk layout as follows:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/ch208r-root
                      230G  707M  218G   1% /
/dev/sda1             274M   17M  243M   7% /boot
/dev/mapper/ch208r-opt+amanda
                      564G  422M  535G   1% /opt/amanda
/dev/mapper/ch208r-tmp
                      4.7G  138M  4.4G   4% /tmp
/dev/mapper/ch208r-var
                      4.7G  264M  4.2G   6% /var

```

I dont understand what this "500 9000 5000 ext3  " meaning.

Thanks

---

