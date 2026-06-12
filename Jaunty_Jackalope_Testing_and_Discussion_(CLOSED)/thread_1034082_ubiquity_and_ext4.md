---
title: "ubiquity and ext4"
date: 2009-01-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2009-01-07
Hi all, 
    Now we need support in ubiquity to have ext4 support. 

AFAIK ubiquity uses debian-installer code as well as libparted. 

Now dunno how much support is there or needed in debian-installer but seems to have some initial support in libparted. 

[http://parted.alioth.debian.org/cgi-bin/trac.cgi/ticket/188](http://parted.alioth.debian.org/cgi-bin/trac.cgi/ticket/188)

I guess we get it as and when libparted 1.8.9 is done. 

[http://parted.alioth.debian.org/cgi-bin/trac.cgi/query?status=new&status=assigned&status=reopened&milestone=1.8.9](http://parted.alioth.debian.org/cgi-bin/trac.cgi/query?status=new&status=assigned&status=reopened&milestone=1.8.9)

The libparted version which we have is seems to be 1.8.8.git.2008.03.24-11.1ubuntu1

```

$ aptitude show libparted1.8-10
Package: libparted1.8-10
New: yes
State: installed
Automatically installed: yes
Version: 1.8.8.git.2008.03.24-11.1ubuntu1
Priority: standard
Section: libs
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 467k
Depends: libc6 (>= 2.8), libdevmapper1.02.1 (>= 2:1.02.20), libuuid1 (>= 1.05)
Suggests: parted | nparted, libparted1.8-dev, libparted1.8-i18n (=
          1.8.8.git.2008.03.24-11.1ubuntu1)
Conflicts: libparted0, libparted1, libparted2, parted (< 1.4.13+14pre1)
Replaces: libparted0, libparted1, libparted1.4 (< 1.4.24-2), libparted2
Provides: libparted
Description: The GNU Parted disk partitioning shared library
 GNU Parted is a program that allows you to create, destroy, resize, move and copy hard disk
 partitions. This is useful for creating space for new operating systems, reorganising disk
 usage, and copying data to new hard disks. This package contains the Parted binary and manual
 page. 
 
 This package contains libparted, the required shared library used by Parted. 
 
 Parted currently supports DOS, Mac, Sun, BSD, GPT, MIPS and PC98 disklabels/partition tables, as
 well as a 'loop' (raw disk) type which allows use on RAID/LVM. Filesystems which are currently
 fully supported are ext2, ext3, fat (FAT16 and FAT32), ReiserFS (with libreiserfs) and
 linux-swap. Parted can also detect and remove HFS (Mac OS), JFS, NTFS, UFS (Sun and HP), XFS and
 ASFS/AFFS/APFS (Amiga) filesystems, but cannot create, resize or check these filesystems yet. 
 
 Note that ReiserFS support is only enabled if you install the libreiserfs0.3-0 package. Since
 libreiserfs0.3-0 has been removed from sarge, ReiserFS support is not compiled in the default
 package. 
 
 The nature of this software means that any bugs could cause massive data loss. While there are
 no known bugs at the moment, they could exist, so please back up all important files before
 running it, and do so at your own risk.

```

---

### Post by cjwatson on 2009-01-08
It's all done in jaunty now (well, I haven't uploaded the changes to ubiquity yet, but they're done for the next upload).

---

### Post by Eclipse. on 2009-01-08
> **cjwatson said:**
> It's all done in jaunty now (well, I haven't uploaded the changes to ubiquity yet, but they're done for the next upload).

Great news, just seen the changes in the bzr branch.

Nice work.;)

---

### Post by Eclipse. on 2009-01-08
> **cjwatson said:**
> It's all done in jaunty now (well, I haven't uploaded the changes to ubiquity yet, but they're done for the next upload).

Great news, just seen the changes in the bzr branch.

Nice work.;)

---

### Post by int on 2009-01-08
> ubiquity (1.11.2) jaunty; urgency=low

 * Adjust for changes in tzsetup 1:0.24ubuntu1.
 * Correct Bazaar link in debian/copyright (pointed out by shirish).
 * Make sure that only one of grub and lilo is installed (LP: #314004).
 * Add ext4 support (LP: #293465).
 * Automatic update of included source packages: apt-setup 1:0.37ubuntu7,
   hw-detect 1.71ubuntu3, partconf 1.30build1, partman-auto 83ubuntu2,
   partman-base 128ubuntu4, partman-ext3 55ubuntu2, partman-partitioning
   64ubuntu2, partman-target 58ubuntu2, tzsetup 1:0.24ubuntu1, user-setup
   1.23ubuntu6.

Date: Thu, 08 Jan 2009 18:40:19 +0000
Changed-By: Colin Watson <cjwatson@ubuntu.com>
Maintainer: Ubuntu Installer Team <ubuntu-installer@lists.ubuntu.com>
Signed-By: Colin Watson <cjwatson@canonical.com>
[https://launchpad.net/ubuntu/jaunty/+source/ubiquity/1.11.2](https://launchpad.net/ubuntu/jaunty/+source/ubiquity/1.11.2)
.......
goood

---

### Post by Slug71 on 2009-01-08
Excellent News!! Thanks Devs! :D:D

---

### Post by hanasaki on 2009-01-24
Is there a gparted / parted that supports ext4?

---

### Post by Gourgi on 2009-01-25
> **hanasaki said:**
> Is there a gparted / parted that supports ext4?
there is , but in svn 
not yet in jaunty
hopefully will see it coming :D

---

### Post by Gina on 2009-01-25
Yes, it's a "must have" if we want to do much with ext4 beyond installing with it.

---

