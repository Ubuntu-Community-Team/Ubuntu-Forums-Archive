---
title: "Error 22: No such partition&quot; in Dual Boot"
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by RoyBot on 2008-09-29
I've been able to (finally) successfully install Ubuntu on a disk that also includes 2 Windows XP installs.

Unfortunately, when I run GRUB at boot-time, I get a **ERROR 22: No Such Partition** message:

```

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbded029d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       25496   204796588+   7  HPFS/NTFS
/dev/sdb2           25497       50992   204796620    f  W95 Ext'd (LBA)
/dev/sdb3           50993       60315    74886997+  83  Linux
/dev/sdb4           60316       60801     3903795   82  Linux swap / Solaris
/dev/sdb5           25497       50992   204796588+   7  HPFS/NTFS


```

Here's what the Grub section looks like:

```

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=44d49ea9-f17b-4f57-a2e8-8d9b0f0e7b80 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=44d49ea9-f17b-4f57-a2e8-8d9b0f0e7b80 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet


```

Any help much appreciated.

Thanks

---

### Post by Pumalite on 2008-09-29
Where is sda?

---

### Post by RoyBot on 2008-09-29
It's a (big) Windows data drive...

```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ef3e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121601   976760001    7  HPFS/NTFS

```

---

### Post by Pumalite on 2008-09-29
Maybe your Grub got installed there. Try changing the boot order in BIOS

---

### Post by RoyBot on 2008-09-29
Grub loads okay.  But the Error 22 comes up when I select the Ubuntu option in the Grub menu.

---

### Post by Pumalite on 2008-09-29
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by tad1073 on 2008-09-29
I was having the same problem, but I figured out a work around for it.

I have 1 ide ata drive and 3 scsi drives on an scsi controler. 

What I did was unpluged the scsi controler, booted the install disk, installed then shut down pluged the scsi contrler back in booted and formated the disks attached to the controler.

Not pretty but it worked.

---

### Post by RoyBot on 2008-09-29
Wow, nearly 200 posts!  But no single instance of Error 22 found...  Perhaps the error is not with Grub?

---

### Post by Pumalite on 2008-09-29
Grub cannot find the partition. Read the link I gave you.

---

### Post by RoyBot on 2008-09-29
wading through it now...

---

### Post by RoyBot on 2008-09-29
I was able to get it working by tinkering with the HD entries.  Ultimately, (hd0,2) worked, while (hd1,2) the output from the grub find entry was causing the error.

Thank you for your help!

Hopefully this thread will help others in the future...

---

### Post by 73ckn797 on 2008-09-30
> **RoyBot said:**
> I was able to get it working by tinkering with the HD entries.  Ultimately, (hd0,2) worked, while (hd1,2) the output from the grub find entry was causing the error.

Thank you for your help!

Hopefully this thread will help others in the future...


Sounds similar to the issue I have been talking about:
[http://ubuntuforums.org/showthread.php?t=932692](http://ubuntuforums.org/showthread.php?t=932692)

---

