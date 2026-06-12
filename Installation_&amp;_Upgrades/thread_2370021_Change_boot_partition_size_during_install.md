---
title: "Change boot partition size during install"
date: 2017-08-29
forum: Installation &amp; Upgrades
---

### Post by dbcrvl on 2017-08-29
Hi,

I need to install Ubuntu 16.04 on many computers and need to **change the /boot partition size to be 4GBs** (from the default 512MB) on all of them. The computers have to use **EFI and LVM** (for the /swap and / partitions).

Ubuntu installs and works fine with the defaults (but /boot is only 512MB!).

I am trying to use partman-auto/expert_recipe with the below string, but it does not work as I get an error at the end of the installation process saying:[INDENT]*the 'grub-efi-amd64-signed' package failed to install into /target/.  Without the GRUB boot loader, the installed system will not boot.*
[/INDENT]

This is the recipe I am using:

```

[FONT=lucida console]d-i partman-auto/expert_recipe string boot-root ::            \
      1 1 1 free                              \
         $bios_boot{ }                        \
         method{ biosgrub } .                 \
      256 256 256 fat32                       \
         $primary{ } $lvmignore{ }            \
         method{ efi } format{ } .            \
      4096 4096 4096 ext3                     \
         $primary{ } $bootable{ }             \
         method{ format } format{ }           \
         use_filesystem{ } filesystem{ ext3 } \
         mountpoint{ /boot } .                \
      40000 430000 -1 ext4                    \
         $lvmok{ }                            \
         method{ format } format{ }           \
         use_filesystem{ } filesystem{ ext4 } \
         mountpoint{ / } .                    \
      16384 16384 16384 linux-swap            \
         $lvmok{ }                            \
         method{ swap } format{ } .[/FONT]

```

What can be causing this?

**Or maybe there is an easier way to resize the /boot partition without a recipe?**

Thanks!

---

### Post by Dennis N on 2017-08-29
> I need to install Ubuntu 16.04 on many computers and need to change the /boot partition size to be 4GBs (from the default 512MB) on all of them. The computers have to use EFI and LVM (for the /swap and / partitions). Ubuntu installs and works fine with the defaults (but /boot is only 512MB!).


Is there a reason for a boot partition at all? 

**UEFI + LVM + no encryption** requires no boot partition in Ubuntu. I use only a root LV with boot folder part of that. 

Prepare disk with necessary structure before installing. When installing, use "Something Else" option, and any prepared logical volume(s) will be at the top of the partitioning screen.

---

### Post by TheFu on 2017-08-29
I would "do something else" for the install and create /boot and /boot/efi and a WASTED partition in sequence. Make the WASTED size 4G.  Then make the partition for all the LVM stuff with the remaining storage.

After the fact, you can remove WASTED and resize /boot and /boot/efi as you desire.

After everything was setup the way I wanted/needed, I'd clone that disk to all the others.
Just remember to change the hostname, and rerun the system encryption salt stuff. Wouldn't be good to have too many systems with the same salts.

---

### Post by dbcrvl on 2017-08-30
Thanks all, I just created a EFI partition, a swap partition and the /  partition, not using LVM any more, so all good now, thanks!

---

