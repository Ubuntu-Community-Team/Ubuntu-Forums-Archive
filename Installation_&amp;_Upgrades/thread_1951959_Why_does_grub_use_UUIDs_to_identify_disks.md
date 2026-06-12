---
title: "Why does grub use UUIDs to identify disks?"
date: 2012-04-03
forum: Installation &amp; Upgrades
---

### Post by shumifan50 on 2012-04-03
What is the benefit of grub using UUIDs to find boot/swap etc disks. These disks can be found equally well just using the device name. It causes problems when the UUID of  disk changes, e.g. I did an install and then restored a tarball from another install, hoping to create a duplicate server (different disk sizes and clonezilla failed). This overwrote /etc/fstab and /boot/grub/grub.cfg with the version from the first installation and so caused the boot process to fail with disk not found.
I corrected the problem by removing the UUIDs from fstab and grub.cfg and now it all works fine.
So to me it seems like these UUIDs for the disks cause more problems than they solve.

---

### Post by SeijiSensei on 2012-04-03
The device names are even more subject to change than UUIDs. If you have a USB mass storage device plugged in, for instance, depending on how the BIOS assigns device addresses /dev/sdb may no longer be the same device as it was without the USB drive connected.  In contrast,  UUIDs are unique to each partition.

/dev/sda is usually pretty static, but all the other assignments are pretty mutable.

---

### Post by jerome1232 on 2012-04-03
One some machines /dev/sdx arbitraily dance around, even without you adding/removing usb disks. Others will as previously stated dance around depending on if you booted with a usb device inserted or not. This is due to the way the BIOS is ordering the drives.


uuid stays constant unless you explicitly change it, or reformat a partition etc. UUID, or filesystem labels, is a more robust way to handle these situations.

---

### Post by coffeecat on 2012-04-03
Your use of a tarball to "clone" a system is exactly what I do on occasion, but it's very much a minority scenario. UUIDs are much better for identifying partitions for the reasons the two previous posters have described.

---

### Post by shumifan50 on 2012-04-03
Thanks for the replies. This is quite true for desktops, but I use HP Proliant servers and the disks off the RAID controller are called /dev/cciss/cxdxpx and these are not affected by adding USB or even SATA devices, so UUIDs buy me nothing but will further cause me pain if a disk fails and I have to replace it (hotswap).
As a matter of interest for those that get burnt:
The 2 files that need fixing are:
/etc/fstab (fixes mounts)
/boot/grub/grub.cfg to fix where to boot from.

As a further question: Is there any way to set the UUID of a partition to a specific value?

---

### Post by CharlesA on 2012-04-03
[http://nixcraft.com/shell-scripting/948-change-uuid-ext3-partition.html](http://nixcraft.com/shell-scripting/948-change-uuid-ext3-partition.html)

---

### Post by coffeecat on 2012-04-03
> **shumifan50 said:**
> 
As a further question: Is there any way to set the UUID of a partition to a specific value?

Have a look at man tune2fs. The code below works for non-raid partitions - I assume it will work if you have RAID set up.

```
sudo tune2fs -U UUID device
```

---

### Post by jerome1232 on 2012-04-03
Depends on the filesystem, assuming extx, see man tune2fs for details, or check your specific filesystem tools.

```
# tune2fs -U "blurb-bloop-bah!" /dev/devicehere
```

edit: out typed!

---

### Post by Punica on 2012-04-03
The company I work for has situations where disks jump around in systems a lot, so /dev/sdX is not sufficient anymore. 

We didnt like UUID's either because they're just to non-human-readable. What we did was link all our configs to disk-by-id, this identifies the disk to its serialnumber so you always know you're 100% sure doing X to disk X and not something else.

Tbh I dont understand why "linux" didnt go for this approach in the first place as serialnumbers are always unique.

---

### Post by shumifan50 on 2012-04-03
coffeecat: thanks for that. It can take away some of the pain as rather than editing the files I can just reset the UUIDs.

---

