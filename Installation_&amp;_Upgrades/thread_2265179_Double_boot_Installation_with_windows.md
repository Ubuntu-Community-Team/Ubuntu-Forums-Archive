---
title: "Double boot Installation with windows"
date: 2015-02-13
forum: Installation &amp; Upgrades
---

### Post by sam9999it on 2015-02-13
Hi, i'm using ububtu gnome on a VM and I'm enough soddisfact of it work.
Then now I'll like to try ubuntu gnome on the base machine, but there's windows 8.
All entire HD is patitioned NTFS. I like to try on the base machine for see how ubuntu gnome work.
Can I install ubuntu on that HD, preserving the windows installation and data, and starting in multiboot the base machine? 
Or have I to format all and make a double partiotion, one for ubuntu and one for windows?

---

### Post by cl-netbox on 2015-02-13
Boot from ubuntu live media and open GParted.
Shrink one partition to a size leaving about 20-30 GB unallocated for ubuntu.
Depending on RAM create a new patition sized the same amount or higher and format it to Linux Swap.
Create another new partition sized about 16GB and format it to Ext4.
Start the installation process, choose 'something else' and install ubuntu to the partition created before.
Install GRUB on the same disk where the ubuntu root partition will be installed.

---

### Post by Mark Phelps on 2015-02-13
Do NOT, repeat NOT, use GParted to shrink the Windows OS partitions.  Doing so has been known to cause filesystem corruption in Windows and rendering it unbootable.

Instead, use the Windows Disk Management tool to do the shrinkage.

---

