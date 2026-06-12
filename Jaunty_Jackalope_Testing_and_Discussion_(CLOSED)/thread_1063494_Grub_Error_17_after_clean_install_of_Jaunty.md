---
title: "Grub Error 17 after clean install of Jaunty"
date: 2009-02-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by airbornemist6 on 2009-02-07
I just decided to wipe my Intrepid install (it was having some major problems) and install Jaunty. Everything went fine and then all of a sudden, I reboot and get a grub error 22. When I tried choosing a boot drive from the list, I get a grub error 17 when I choose my hd0. I have tried reinstalling Jaunty, restoring grub, everything. No luck. Here's my fdisk -lu if anyone wants it:
```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbd9ca562

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x51cee735

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           51857       60802    71851008    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3dab189

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60762   488070733+  83  Linux
/dev/sdc2           60763       60801      313267+   5  Extended
/dev/sdc5           60763       60801      313236   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbd9ca562

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1953521663   976759808    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x51cee735

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1       833069056   976771071    71851008    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3dab189

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   976141529   488070733+  83  Linux
/dev/sdc2       976141530   976768064      313267+   5  Extended
/dev/sdc5       976141593   976768064      313236   82  Linux swap / Solaris

```

---

### Post by hikaricore on 2009-02-07
Jaunty questions go in the Jaunty forum..

---

### Post by airbornemist6 on 2009-02-07
Oh yeah sorry, long day, my bad, could you move it please?

EDIT: Nevermind, you already did xD

---

### Post by airbornemist6 on 2009-02-08
Just managed to fix this. Not entirely sure how. I just kind of poked the BIOS drives into submission. Now, the next problem, the nvidia 180 drivers broke. I get thrown to terminal on login. But that's for another thread.

---

