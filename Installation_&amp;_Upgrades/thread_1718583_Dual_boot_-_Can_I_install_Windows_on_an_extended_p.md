---
title: "Dual boot - Can I install Windows on an extended partition?"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by SnoopFogg on 2011-03-31
I bought a PC with Window Vista on it as my partner needs it. Using gparted I set up Primary partitions for Vista OS (sda1) and Ubuntu OS (sda2), plus an extended partition for Vista files, Ubuntu /home and swap:

fdisk -l
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3969    31880961    7  HPFS/NTFS
/dev/sda2            3970        5294    10643062+  83  Linux
/dev/sda3            5295       38913   270044617+   5  Extended
/dev/sda5           38126       38913     6329610   82  Linux swap / Solaris
/dev/sda6            5295       18348   104856192    7  HPFS/NTFS
/dev/sda7           18349       38125   158858721   83  Linux

My problem is Vista (as always).  The 30GB I allocated is not enough, even just for the OS and it won't now boot from GRUB, though I can see it from GRUB.  

I don't want to do anything that risks a problem for Ubuntu.  Will grub still see both OS if I wipe sda1 (Vista OS) and reinstall Vista OS on the extended partition sda6?

Ideally I would like to merge sda1 with sda6 and install Vista on that, but that looks way too risky / impossible.  

Any advice would be much appreciated.
____
Edit - There is another drive on the PC which is much larger and I use for backup.  Is there any scope for installing Vista on that one so that GRUB still identifies both.  Not ideal as I like having one as the backup for the other.

---

### Post by dabl on 2011-03-31
I've never heard of Windows being booted and run from a logical partition -- I'm pretty confident it needs to be on a primary partition (or else on a VM).

On the other hand, Linux doesn't mind being on a logical partition within an extended partition.  So, if you can re-arrange things, you could install Linux in the extended partition and leave the primary partitions for Windows.

---

### Post by garvinrick4 on 2011-03-31
I am under the belief that Windows is at it's happiest in a Primary partition. Where as Linux is
happy to exist anywhere she can.

---

### Post by SnoopFogg on 2011-03-31
Thanks for the advice.  Guess I need to move stuff around.

Cheers

---

### Post by oldfred on 2011-03-31
Windows has to boot from a primary partition, but if a second install that can be a logical partition. But if you ever delete the first install in the primary the second in the logical is not bootable not repairable.

Always best to install all windows systems to primary partitions.

---

