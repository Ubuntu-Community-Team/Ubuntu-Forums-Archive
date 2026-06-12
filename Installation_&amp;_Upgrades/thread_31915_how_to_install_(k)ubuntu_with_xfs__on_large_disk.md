---
title: "how to install (k)ubuntu with xfs / on large disk"
date: 2005-05-05
forum: Installation &amp; Upgrades
---

### Post by tariq on 2005-05-05
i am finally making the move from mandrake and mandriva to (k)ubuntu.

however i'm having some problems during the install when it wants to install GRUB.

i have a laptop (del 8600) with an 80Gb hard disk. the first 2 primary partitions are taken and cannot be resized/moved. then i have a series of logical paritions  .. previously the last one (about 30Gb) was housing mandrake for various versions, running over xfs.

now, i know that people say i shouldn't be bale to boot a linux with grub if it is all on  an xfs / (with no ext2 /boot). but it worked flawlessly with mandrake - and various versions of mandrake including 10.1 and the 2005LE. 

after the installer hangs on "bootloader installing 50%" for a logn time i kill -9 the grub processes and finish the installation without a grub to the MBR.

the previous grub from mandrake drops me nicely intio a CLI from where i can easily boot ubuntu ... (root, kernel, initrd) ... 

so grub CAN see xfs and its contents.

installing from a chroot fails, as does installing it during a booted ubuntu session.

why the problem?

constraints - LILO and a new /boot are not an option.

can this be done? what magic did the mandrake installer do?

---

### Post by sprucio on 2005-05-05
I believe bootloaders (GRUB, or LILO) can't boot from a logical partition?

Isn't this why distros like FC always installs a boot partition on a primary partition?

---

### Post by nad on 2005-05-05
Grub does support xfs. The debian/ubuntu version does not.

---

