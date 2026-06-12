---
title: "Why debootstrap can't use Desktop CD as package source?"
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by GeoMX on 2010-09-07
I'm running Karmic Desktop Live CD from a USB stick, and trying to install Ubuntu to a hard disk using debootstrap I get these errors:

$ sudo debootstrap karmic /dir file:///cdrom/
> 
I: Retrieving Release
I: Validating Packages
I: Resolving dependencies of required packages...
I: Resolving dependencies of base packages...
W: Failure trying to run: chroot /dir mount -t proc proc /proc


$ cat /dir/debootstrap/debootstrap.log 
> 
ar: /dir/: File format not recognized

gzip: stdin: unexpected end of file
chroot: cannot run command `mount': No such file or directory
ar: /dir/: File format not recognized

gzip: stdin: unexpected end of file
chroot: cannot run command `mount': No such file or directory
ar: /dir/: File format not recognized

gzip: stdin: unexpected end of file
chroot: cannot run command `mount': No such file or directory
ar: /dir/: File format not recognized

gzip: stdin: unexpected end of file
chroot: cannot run command `mount': No such file or directory
ar: /dir/: File format not recognized

gzip: stdin: unexpected end of file
chroot: cannot run command `mount': No such file or directory

I've read this bug report: [https://bugs.launchpad.net/ubuntu/+source/debootstrap/+bug/77589](https://bugs.launchpad.net/ubuntu/+source/debootstrap/+bug/77589) basically, the discussion states that Desktop CD can not be used as package source for debootstrapping, I understand it is because of different file structure than the required for a repository, but would like to know more specific information about it, and if possible, how could I use the CD as package source for debootstrap?

Thanks.

---

### Post by slakkie on 2010-09-07
Think you should use the alternate CD if you want to use it as a package source.

---

