---
title: "What could prevent Grub from working?"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by Bloodypriest on 2006-10-27
Hi,

I recently upgraded from Dapper to Edgy. I reinstalled from scratch because I wanted to change partition types from ReiserFS to XFS and go back from x64 to x86.

First, a little more background about my setup. I am installing Edgy on an Nvidia fakeraid (which has a bug in the bios) so the Dmraid version provided in the repositories did not work. I first had to get the updated version from here: [https://launchpad.net/bugs/54246](https://launchpad.net/bugs/54246). After that, I did everything according to the Fakeraid howto EXCEPT I had to create the fstab BEFORE doing the apt-get whatever (otherwise, dbus wouldn't install correctly). I also installed the updated dmraid instead of the one that was in the repositories.

Next came the GRUB installation. Here's what I've done:

grub

device (hd0) /dev/mapper/nvidia_ccegahad
geometry (hd0) 29186 255 63
root (hd0,0)
setup (hd0,0)
quit

The first partition of the hard disk was already activated since I had a previous Dapper installation. I reboot and I the only thing I got was the dreaded "Error loading operating system". What could have gone wrong?

---

### Post by Bloodypriest on 2006-10-28
Finally found an answer, don't know if it is the right but it is an answer.

[quote="SUSE LINUX Administration Guide 9.3"]
**GRUB and XFS**

    XFS leaves no room for stage1 in the partition boot block. Therefore, do not specify an XFS partition as the location of the boot loader. This problem can be solved by creating a separate boot partition that is not formatted with XFS. 

**GRUB and JFS**

    Alhough technically possible, the combination of GRUB with JFS is problematic. In this case, create a separate boot partition (/boot) and format it with Ext2. Install GRUB in this partition. 
[/quote]

---

