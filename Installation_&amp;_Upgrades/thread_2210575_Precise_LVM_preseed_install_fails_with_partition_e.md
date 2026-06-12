---
title: "Precise LVM preseed install fails with partition error"
date: 2014-03-11
forum: Installation &amp; Upgrades
---

### Post by sandeep-raman on 2014-03-11
[FONT=arial]I am using a preseed file to install Precise 12.04.4 on a physical server with the following requirement:

[LIST]
[*]The 146gb disk need to be partitioned as 120gb '/' partition and 25gb 'swap' partition with lvm.
[/LIST]

The install fails with the error "Description: Failed to partition the selected disk[/FONT][FONT=arial] This happened because the selected recipe does not contain any partition [/FONT][FONT=arial] that can be created on LVM volumes."[/FONT]
[FONT=arial]
The following lines from the preseed specific to disk configuration:
> 
[/FONT][FONT=arial]d-i partman-auto/disk string /dev/sda[/FONT]
[FONT=arial]d-i partman-auto/method string lvm[/FONT]
[FONT=arial]d-i partman-lvm/device_remove_lvm boolean true[/FONT]
[FONT=arial]d-i partman-lvm/device_remove_lvm_span boolean true[/FONT]
[FONT=arial]d-i partman-md/device_remove_md boolean true[/FONT]
[FONT=arial]d-i partman-lvm/confirm boolean true[/FONT]
[FONT=arial]d-i partman/choose_partition select finish[/FONT]
[FONT=arial]d-i partman-lvm/confirm_nooverwrite boolean true[/FONT]
[FONT=arial]d-i partman-auto-lvm/guided_size string max[/FONT]
[FONT=arial]d-i partman-auto/choose_recipe select root_swap[/FONT]
[FONT=arial]d-i partman/default_filesystem string ext4[/FONT]
[FONT=arial]d-i partman-partitioning/confirm_write_new_label boolean true[/FONT]
[FONT=arial]d-i partman/confirm boolean true[/FONT]
[FONT=arial]d-i partman/confirm_nooverwrite boolean true[/FONT]
[FONT=arial]d-i partman-auto/expert_recipe string root_swap :: \[/FONT]
[FONT=arial]120000 10 120000 ext4                             \[/FONT]
[FONT=arial]    $defaultignore{ }[/FONT]
[FONT=arial]    $lvmok{ } lv_name{ root }                   \[/FONT]
[FONT=arial]    method{ format } format{ }                  \[/FONT]
[FONT=arial]    use_filesystem{ } filesystem{ ext4 }        \[/FONT]
[FONT=arial]    mountpoint{ / }[/FONT]
[FONT=arial]    [/FONT]
[FONT=arial]25000 20 25000 linux-swap                       \[/FONT]
[FONT=arial]    $lvmok{ } lv_name{ swap_1 }                 \[/FONT]
[FONT=arial]    method{ swap } format{ }[/FONT]
[FONT=arial]

Is any other option needed in the preseed for this to work?

Cheers,
Sandeep.[/FONT]

---

