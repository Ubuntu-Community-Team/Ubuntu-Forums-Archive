---
title: "diskutils tells me filesystem is not clean and gparted check says its ok"
date: 2014-02-08
forum: Installation &amp; Upgrades
---

### Post by robire on 2014-02-08
checked a hd with ubuntu istallation DVD and
don't know what happens.
diskutils tells me filesystem is not clean and gparted check says: all operations succesfully completed ?

so I did:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c5ae2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1953521663   976657408    7  HPFS/NTFS/exFAT


ubuntu@ubuntu:~$ sudo ntfsck /dev/sda1
Unsupported: replay_log()
Unsupported: check_volume()
Checking 256 MFT records.
Unsupported cases found.
ubuntu@ubuntu:~$ sudo ntfsck /dev/sda2
Unsupported: replay_log()
Unsupported: check_volume()
Checking 57856 MFT records.
Unsupported cases found.
ubuntu@ubuntu:~$ 

hmm, what's the meaning of this ?

---

### Post by sudodus on 2014-02-08
The linux tools for Microsoft filesystems are not as good as Microsoft's own tools. I recommend linux tools for linux software (including file systems), and Windows tools for Windows software (including file systems).

Is there any chance that you can use Windows (or maybe Bart PE or Windows 7 PE) to check and if necessary repair the NTFS file systems?

But usually gparted can create NTFS file systems, that work for Windows.

---

### Post by Mark Phelps on 2014-02-08
"Not clean" generally means that the Windows filesystem exited improperly -- which generally can NOT be fixed with Linux filesystem tools.

Your best bet is to boot into Windows and run CHKDSK on the partition.  There is no equivalent utility you can run from Linux that will check and repair the Windows filesystem.

---

### Post by robire on 2014-02-13
I did chkdsk from a windows installation disk, but afterwards I had the same results.

I remembered fdisk at windows installation disk and gave it a try.

That solved my problem.

Thanks to everybody looking after me.

problem solved .

---

