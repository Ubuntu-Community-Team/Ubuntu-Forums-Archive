---
title: "[SOLVED] how to uninstall Window"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by songhk on 2008-01-03
My computer has 2 system ( ubuntu + window).

When I turned on my computer, I saw the screen that I can choose ubuntu or window.

I want to uninstall the window, and want to just use ubuntu.

How to uninstall the window? Please help me...

I'm almost beginner,,,please explain easily. thanks.

---

### Post by Partyboi2 on 2008-01-03
Use gparted and delete the windows partition then resize the ubuntu partition to use the new space.

---

### Post by songhk on 2008-01-04
> **Partyboi2 said:**
> Use gparted and delete the windows partition then resize the ubuntu partition to use the new space.

-----------------------------------------------------------------
Thanks. I have a question:

I run gparted.  I attached my gparted information. 
But I don't know which is the window.
What's is the window partition?




Partition         Filesystem     Mountpoint      Size              Used          Unused       Flags

/dev/sda1     ntfs                                        15.99 GiB      ...               ...                boot
/dev/sda2     ext3                /                       11.05 GiB     4.12 GiB     6.94 GiB                     
/dev/sda4     extended                                545.10 MiB   ...               ...     
/dev/sda5     linux-swap                             549.07 MiB   ...               ...     
/dev/sda4     linux-swap                             368.68 MiB   ...               ...    
unallocated   unallocated                            15.69 MiB      ...               ...

---

### Post by markusf21 on 2008-01-04
the ntfs partition is windows

---

### Post by PmDematagoda on 2008-01-04
"/dev/sda1 ntfs 15.99 GiB ... ... boot" is the Windows partition.

---

### Post by songhk on 2008-01-04
> **PmDematagoda said:**
> "/dev/sda1 ntfs 15.99 GiB ... ... boot" is the Windows partition.
 -----------------------------------------------------------------

Thanks. I got it. 

I deleted window partition. and made new partitions at there.

---

