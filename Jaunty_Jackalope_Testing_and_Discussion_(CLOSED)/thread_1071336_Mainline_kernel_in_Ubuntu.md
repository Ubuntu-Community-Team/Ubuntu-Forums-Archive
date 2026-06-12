---
title: "Mainline kernel in Ubuntu"
date: 2009-02-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by int on 2009-02-16
Manline kernel release for ubuntu.

> The mainline build for v2.6.27.17 is now complete and available at the URL
below:

   [http://kernel.ubuntu.com/~apw/mainline/v2.6.27.17/](http://kernel.ubuntu.com/~apw/mainline/v2.6.27.17/)

The mainline build for v2.6.28.5 is now complete and available at the URL
below:

   [http://kernel.ubuntu.com/~apw/mainline/v2.6.28.5/](http://kernel.ubuntu.com/~apw/mainline/v2.6.28.5/)

The mainline build for v2.6.29-rc5 is now complete and available at the URL
below:

   [http://kernel.ubuntu.com/~apw/mainline/v2.6.29-rc5/](http://kernel.ubuntu.com/~apw/mainline/v2.6.29-rc5/)

Note that these builds do not contain any Ubuntu specific patches and
are not supported.

Kernel Team

---

### Post by inportb on 2009-02-16
Thanks for posting this thread. It should help both Ubuntu and non-Ubuntu users as they test the latest kernel.

---

### Post by int on 2009-02-17
[http://kernel.ubuntu.com/~apw/mainline/](http://kernel.ubuntu.com/~apw/mainline/)


I have the kernel 2.6.29-rc5 from mainline, and is working fine, it seems to work faster that the 2.6.28.8.

I will test the btrfs-dev.

Steps that I made(64 bits):

1) linux-headers-2.6.29-020629rc5_2.6.29-020629rc5_all.deb
2) linux-headers-2.6.29-020629rc5-generic_2.6.29-020629rc5_amd64.deb	
3) linux-image-2.6.29-020629rc5-generic_2.6.29-020629rc5_amd64.deb

---

### Post by syko21 on 2009-02-17
Does this allow for the possibility of ext4 on the boot partition of intrepid? Assuming the new patched jaunty grub is used.

---

### Post by int on 2009-02-17
> **syko21 said:**
> Does this allow for the possibility of ext4 on the boot partition of intrepid? Assuming the new patched jaunty grub is used.

yes.. but you need also the ext4 dependents, e2fsprogs >=1.41.3,..

[http://ext4.wiki.kernel.org/index.php/Main_Page](http://ext4.wiki.kernel.org/index.php/Main_Page)

---

### Post by Salane on 2009-02-17
> **syko21 said:**
> Does this allow for the possibility of ext4 on the boot partition of intrepid? Assuming the new patched jaunty grub is used.

No problems here using e2fsprogs 1.41.4 


cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump><pass>
proc            /proc           proc    defaults        00
# / was on /dev/sda5 during installation
UUID=8edfcb1b-b484-4542-adf0-84ee62ef3287 /               ext4  relatime,errors=remount-ro 0       1
# /boot was on /dev/sda7 during installation
UUID=cc9cf6be-8432-40ea-a695-a4470032162b /boot           ext4  relatime        0       2
# /home was on /dev/sda8 during installation
UUID=9f7b3b21-bae9-42ef-9646-adc0a3818593 /home           ext4  relatime        0       2
# none was on /dev/sda6 during installation
UUID=ad256edb-2b71-4e37-8b70-4e1f800d8ed7 none            swap  sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Chrisj303 on 2009-02-17
I only update my kernel when I update my whole OS to the newest release (like 8.04 -> 8.10).

Is this bad practice? Should I be updating the kernel as often as possible?

---

### Post by inportb on 2009-02-17
Well, if you don't mind the bugs (or security issues) involved with using old software, there's nothing wrong with that really.

---

