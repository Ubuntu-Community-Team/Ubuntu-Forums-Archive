---
title: "Re-install Windows XP after a crash with XP on a dual boot?"
date: 2011-11-08
forum: Installation &amp; Upgrades
---

### Post by PDA1 on 2011-11-08
My system is dual boot with Windows XP and Ubuntu 10.04.

XP got corrupted and now needs to be re-installed.

How do I re-install Windows XP while keeping my Ubuntu 10.04 intact?

---

### Post by oldfred on 2011-11-09
If your NTFS partition has the boot flag, XP should just reinstall to that partition. The issue will be that it will put the Windows boot loader into the MBR. You then need to reinstall grub2's boot loader from the liveCD. So make sure you have a liveCD of the current version of Ubuntu.

Have you backed up all your data from your XP. Did you run chkdsk or other repairs to see if you can fix it?

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

