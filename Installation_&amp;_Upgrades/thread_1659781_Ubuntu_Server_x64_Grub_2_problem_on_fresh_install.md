---
title: "Ubuntu Server x64 Grub 2 problem on fresh install"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by Twizzle on 2011-01-04
I had Ubuntu server edition 9.04 installed on a system with two HDDs set up as a LVM.

Yesterday I decided to upgrade to 10.10 x64 server edition but thought that a fresh install would be best.

I tried to install with the same LVM setup (allowing the partitions to be formatted) but once installed I got a:

```
GRUB loading.
 error: file not found
```

I thought that it was the LVM causing the problems so removed it and set the two drives as sda for / and swap and sdb for /home.

The installation went fine again but I still get the same GRUB error.

I have tried setting the / partition to ext2 and ext4 bootable and non bootable. Allowing the installer to install grub to the MBR or manually setting it to /dev/sda1 but still with the same error.

If I try to use the grub rescue command line I get the following:

```
set prefix=(hd0,1)/boot/grub
insmod normal
error: file not found
```

It seems to me that grub did not install for some reason and I have no idea why.

I even tried to boot from the Live CD (desktop x64 version)and mount the Linux partition in order to:

```
grub-install /dev/sda
```

which again seems to work but results in the same problem when I reboot.

This is driving me mad so any advice would be welcome!

---

