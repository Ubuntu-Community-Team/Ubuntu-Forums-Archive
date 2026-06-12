---
title: "grub error 29..."
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by fanis on 2008-10-31
Hi all! This is my first post to these excellent forums. 

My system has 2 1TB hard disks. 
On the first I installed windows vista business 32 bit. Everything worked perfectly.
On the other I installed ubuntu 8.1 x86_64. This is where I installed grub as well. 

On the grub menu I can boot ubuntu perfectly, but after the installation vista won't boot. Grub gives error 29. 

Here's some info:
Output of *sudo fdisk -l*
```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ea51733

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x32b460e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       58368   468840928+  83  Linux
/dev/sdb2           58369      116737   468848992+  83  Linux
/dev/sdb3          116738      121601    39070080   82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    c  W95 FAT32 (LBA)


```

Here's my /boot/grub/menu.lst

```

default         0
timeout         10
title           Ubuntu 8.10, kernel 2.6.27-7-generic
uuid            b9259c95-b2ad-4a19-8589-4cee89179434
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=b9259c95-b2ad-4a19-858$
initrd          /boot/initrd.img-2.6.27-7-generic
quiet

title           Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid            b9259c95-b2ad-4a19-8589-4cee89179434
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=b9259c95-b2ad-4a19-858$
initrd          /boot/initrd.img-2.6.27-7-generic

title           Ubuntu 8.10, memtest86+
uuid            b9259c95-b2ad-4a19-8589-4cee89179434
kernel          /boot/memtest86+.bin
quiet

title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1


```

Hope someone figures it out as I'm desparate :) Thanks in advance.

---

### Post by meierfra. on 2008-11-01
Open menu.lst with "gksudo gedit /boot/grub/menu.lst" and remove  "savedefault" from the Windows item in menu.lst:


title           Windows Vista/Longhorn (loader)
root            (hd0,0)
makeactive
chainloader     +1



If this does not work, remove "makeactive"

---

### Post by fanis on 2008-11-01
Worked perfectly. Thank you so much! This is the first time something like this happens and I can't help but wondering why. Could you please explain? 

Once again thank you for solving my problem :)

---

### Post by meierfra. on 2008-11-01
> Could you please explain? 

Windows is the 4th item on your grub menu. Grub starts counting at zero, so it views Windows as number "3".  The "savedefault"  commands tries to write "3" to the file "/boot/grub/default", so that the next time  you boot Windows will be the default  boot.  For whatever reason grub does not seem to be able to write to the file /boot/grub/default during boot up. This produces grub error 29.

Grub only uses the number stored in "/boot/grub/default"  if you use "default saved" in menu.lst.  Since you are using "default 0",   the number written in "/boot/grub/default" is irrelevant and removing "savedefault" from your Windows item does not have any negative consequences.

---

### Post by fanis on 2008-11-02
Thanks for the solution and the explanation!

---

