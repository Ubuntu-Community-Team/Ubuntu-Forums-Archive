---
title: "dpkg --configure -a generating initrd files for packages which are not installed"
date: 2017-12-18
forum: Installation &amp; Upgrades
---

### Post by mathog on 2017-12-18
Xubuntu 14.04.5 LTS. 

Today the software updater went nuts and started generating  files like

```
initrd.img-3.13.0-123-generic

```
in /boot.  Lots, and lots of them.  Unclear if it was acting on packages which were never purged or if it installed them all today.  Eventually using commands like 

```
sudo dpkg --purge --force-all linux-image-extra-3.13.0-123-generic

```
and so forth every single linux-image and linux-header package which was not desired was removed.  The spurious initrd files were manually deleted from /boot.  At that point only the desired files for 3.13.0-132  133 and 137 remained in /boot.  Yet doing:

```
sudo dpkg --configure -a

```
started generating the darn initrd files again.  One of these was initrd.img-3.13.0-119-generic
yet:

```
dpkg --list | grep 3.13.0-119

```
finds nothing.  

So where is dpkg --configure -a picking up this information?  There is nothing in /usr/src that matches, nor
are there any vmlinuz or System.map files in /boot.  The initrd's seem to be coming out of thin air!

How do I fix this?  If I don't the next time an upgrade is installed it is going to do this all over again.

Thanks.

---

### Post by Impavidus on 2017-12-18
First of all, Xubuntu 14.04 is no longer supported. Ubuntu 14.04 is still supported, so the parts that Ubuntu and Xubuntu have in common are supported too, but there are no longer upgrades for the parts that are in Xubuntu 14.04 only and compatibility of upgrades to supported packages with Xubuntu-specific packages is no longer checked. In contrast to Ubuntu LTS releases, Xubuntu LTS releases only have 3 years of support. So I recommend you move on to Xubuntu 16.04.

Your problem doesn't seem particular to Xubuntu and sounds quite interesting, so maybe you want to fix it anyway. In which case, what is the complete output of```
dpkg --list | grep linux-image
ls /boot
```
The package manager maintains a list of all packages with their installation status. Whenever a package is to be installed but is not configured yet, dpkg --configure -a will attempt to configure it by running its configuration script. In case of kernel packages, that includes creating the initrd.img* file. At least, that's how it's supposed to work.

Whenever you use```
sudo dpkg --force-all ...
```expect dirt. So when you move on to 16.04, best to make it a clean install, as that will remove all dirt.

---

### Post by mathog on 2017-12-18
```
dpkg --list | grep linux-image
ii  linux-image-3.13.0-132-generic                        3.13.0-132.181                                      i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-133-generic                        3.13.0-133.182                                      i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-137-generic                        3.13.0-137.186                                      i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-132-generic                  3.13.0-132.181                                      i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-133-generic                  3.13.0-133.182                                      i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-137-generic                  3.13.0-137.186                                      i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
iU  linux-image-generic                                   3.13.0.137.146                                      i386         Generic Linux kernel image
```

Yeah, I know --force-all is a hand grenade, but there really wasn't a lot of choice.  One might think from that list that only 132, 133, or 137 initrd's would be created.  Sadly, not the case.

---

### Post by Impavidus on 2017-12-19
The other kernels are indeed not listed as even partially installed. What's in your /boot?

The ony clean way to get rid of the leftover components of old kernels may be to reistall them, then cleanly uninstall them again. But I assume you already tried cleanly uninstalling them before and that failed.

---

### Post by mathog on 2017-12-20
> **Impavidus said:**
> The other kernels are indeed not listed as even partially installed. What's in your /boot?
```
abi-3.13.0-132-generic
abi-3.13.0-133-generic
abi-3.13.0-137-generic
config-3.13.0-132-generic
config-3.13.0-133-generic
config-3.13.0-137-generic
grub
initrd.img-3.13.0-132-generic
initrd.img-3.13.0-133-generic
initrd.img-3.13.0-137-generic
memtest86+.bin
memtest86+.elf
memtest86+_multiboot.bin
System.map-3.13.0-132-generic
System.map-3.13.0-133-generic
System.map-3.13.0-137-generic
vmlinuz-3.13.0-132-generic
vmlinuz-3.13.0-133-generic
vmlinuz-3.13.0-137-generic


```

There was a warning on today's login 

```
Sorry, a problem occurred while installing software.
Package: linux-firmware 1.127.24

```

This is what happens when I tried to reinstall it...

```
sudo apt-get install linux-firmware
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware is already the newest version.
linux-firmware set to manually installed.
The following packages will be REMOVED:
  linux-headers-3.13.0-132-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 13.2 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 272497 files and directories currently installed.)
Removing linux-headers-3.13.0-132-generic (3.13.0-132.181) ...
Setting up linux-firmware (1.127.24) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-137-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-133-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-132-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-125-generic
grep: /boot/config-3.13.0-125-generic: No such file or directory
WARNING: missing /lib/modules/3.13.0-125-generic
Device driver support needs thus be built-in linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-125-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_tsYjLb/lib/modules/3.13.0-125-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_tsYjLb/lib/modules/3.13.0-125-generic/modules.builtin: No such file or directory
update-initramfs: Generating /boot/initrd.img-3.13.0-123-generic
grep: /boot/config-3.13.0-123-generic: No such file or directory
WARNING: missing /lib/modules/3.13.0-123-generic
Device driver support needs thus be built-in linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-123-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_xwnIoa/lib/modules/3.13.0-123-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_xwnIoa/lib/modules/3.13.0-123-generic/modules.builtin: No such file or directory
update-initramfs: Generating /boot/initrd.img-3.13.0-119-generic
grep: /boot/config-3.13.0-119-generic: No such file or directory
WARNING: missing /lib/modules/3.13.0-119-generic
Device driver support needs thus be built-in linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-119-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_lIGF0p/lib/modules/3.13.0-119-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_lIGF0p/lib/modules/3.13.0-119-generic/modules.builtin: No such file or directory
update-initramfs: Generating /boot/initrd.img-3.13.0-116-generic
grep: /boot/config-3.13.0-116-generic: No such file or directory
WARNING: missing /lib/modules/3.13.0-116-generic
etc.

```

Interrupted it with ^C.

it left a bunch of initrd's in /boot.  These were deleted manually.  Note it did the right thing for the 3 versions of the kernel which are supposed to be there.  Then it somehow got it into its head to build all the others.  Beats me where it is getting those version numbers.  In /usr/src and /lib/modules there are only the 3 expected ones.

In boot:

```
sudo grep -R 3.13.0-116 .

```

finds nothing.  Nor does it match anything in /etc.  In /var there are some hits.  /var/lib/dpkg/available and /var/lib/dpkg/available_old list those packages.  Which is correct, I think, since they are in fact available.
some package names match.  Ah, I think I found it.  in /var/lib/initramfs-tools there are files with names corresponding to all the versions which it tries to build again.  Removed all but the desired 3.

At that point 

```
sudo apt-get install linux-firmware 

```

would not start, it demanded that this be run

```

sudo dpkg --configure -a
```

So it was.  This time it did NOT build all the unwanted initrd's.  At that point it was able to run

```
sudo apt-get install linux-firmware 

```

which only built the 3 desired initrd's.

I think maybe this system is now out of the woods.

---

### Post by Impavidus on 2017-12-20
That may indeed have fixed it. update-initramfs keeps a list of initramfs archives, which apparently was corrupted. Maybe some upgrade that got interrupted? I think it would have been possible to use update-initramfs directly to remove those archives.```
sudo update-initramfs -d -k <version>
```I think it's OK now, but still keep in mind that Xubuntu 14.04 is only partially supported, so plan on moving to a supported release. Normal Xubuntu releases have 9 months support, LTS releases 3 years.

Can you mark this thread as solved? Thread tools -> mark as solved.

---

### Post by mathog on 2017-12-21
Marked as solved.  Thanks for your help.

---

