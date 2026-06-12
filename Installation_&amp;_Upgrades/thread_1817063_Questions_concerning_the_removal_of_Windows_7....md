---
title: "Questions concerning the removal of Windows 7..."
date: 2011-08-02
forum: Installation &amp; Upgrades
---

### Post by DarthAceris on 2011-08-02
I've been dual booting Ubuntu 11.04 and Windows 7 for some time, and I was wondering if there is anyway to completely remove Windows without having to do a clean install of Ubuntu. 

Windows is more or less useless to me now, and I've put a lot of time and effort getting Ubuntu running perfectly, so I want to avoid starting fresh at all costs.

---

### Post by FormatSeize on 2011-08-02
Get a utility like Hiren's Boot CD or Gparted, or even a Ubuntu Live CD. Use a partition editor to delete the Windows partition. Then expand the Ubuntu partition to fill the left over space. 

There's a little more to it than that, but that's the general idea. It's nothing that doesn't spell itself out once you start the process of doing it. Too, make sure that GRUB is your default bootloader.

---

### Post by EkuquoL on 2011-08-02
Just use the Disk Utility and delete the Windows Partition.

---

### Post by Furball588 on 2011-08-02
Why not use what's already available to you in Ubuntu?  or even the livecd you installed from?  Only requirement for the partition manager is that the partition you want to deal with is not mounted.  

and yea...it's nothing more then deleting the partition.  If you do your housekeeping, you'll also want to remove the entry from your grub.conf.

Post the results of an fdisk -l, so we can see what your partitioning is like currently.  You don't want to necessarily hose your boot sector if you remove windows.

---

### Post by YannBuntu on 2011-08-03
Hi all,

there is now a tool to uninstall any operating system in 1 clic : OS-Uninstaller  :guitar:

See here: [http://ubuntuforums.org/showthread.php?t=1769489](http://ubuntuforums.org/showthread.php?t=1769489)

[[img]http://pix.toile-libre.org/upload/img/1299159724.png[/img]](http://pix.toile-libre.org/?img=1299159724.png)

---

