---
title: "Dual Booting?"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by wheels5894 on 2007-05-14
I am very keen to try out Ubuntu 7, especially as it now reads NTFS partitions. However, I only have one machine available and that it running Windows XP. I have a second partition on drive 0 that could be used to install Ubuntu and dual boot but this does not look easy.

Is this a sensible idea for a Noob to try and if so where can I find directions to help me do this. 

Thanks

Robert

---

### Post by aquavitae on 2007-05-14
Its fairly easy - in fact I think the Ubuntu installer will do that automatically!  I think the easiest might be the following:
1. Delete the second partition in windows.  This will create free space which Ubuntu can the partition automatically.
2. Run the ubuntu install.  When it asks about partitioning, tell it to use the largest free space available.
3. Ubuntu will install.

When you restart, you will be presented with a boot loader offering to start either Ubuntu or Windows.

A word of warning: Windows doesn't like Linux.  If you ever have to reinstall windows, it will wipe out the bootloader, and possibly the linux partition as well.  I always use a completely different drive so that if I have to reinstall windows I can first disconnect my linux drive.  If you choose to do this, make the linux drive the master, or the bootloader won't be loaded.

---

