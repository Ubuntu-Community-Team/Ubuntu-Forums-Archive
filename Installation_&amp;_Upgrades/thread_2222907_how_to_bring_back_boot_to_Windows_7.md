---
title: "how to bring back boot to Windows 7"
date: 2014-05-08
forum: Installation &amp; Upgrades
---

### Post by mark_galeck2 on 2014-05-08
Hello,

I had (hope still have) Win 7 installation on my machine, and I installed Ubuntu 13 to dual boot, and dual boot worked but I noticed that Ubuntu was 32 bits and this is 64 bit machine.  So I reinstalled Ubuntu 64-bits version 14.

During the installation, Ubuntu asked me where it should install, and I pointed to the old Ubuntu 13 installation, it warned me that installation would be wiped out, I said yes.


But now I can't boot Windows 7.  I hope it is still there.  


By the way, this should not be happening.  Without any warning, Ubuntu installation wiped out ability to boot to an existing system.  That is terrible, I thought, Ubuntu was a good system.  Not with that kind of damage-without-warning.

---

### Post by Mark Phelps on 2014-05-08
>  it warned me that installation would be wiped out,Unfortunately, folks have been reporting that, in some cases, the installer sees this as permission to erase the drive and install from scratch --  not just the Ubuntu partition(s), but everything.

To find out what partitions are still there, boot into Ubuntu, open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one). That will list out the partitions and filesystems and we will at least see if the Windows partition(s) still exist.

---

### Post by oldfred on 2014-05-08
Often wording is not updated even though that is a major issue. It is not a bug in the software as erase entire drive is what was intended.

 Reinstall says overwrite Ubuntu but it also erases existing Windows.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

