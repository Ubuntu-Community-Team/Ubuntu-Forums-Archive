---
title: "problem getting grub to boot partition"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by pldobs on 2008-05-18
I had ubuntu 8.04 on sda1, I messed up my wireless network.  I installed another installation of ubuntu 8.0.4 on sda6.  At that point, I could boot to either sda1 or sda6 with grub.  After configuring the copy on sda6 with all my files from the sda1 partition, I used gparted to copy my sda6 partition over sda1.  Now grub won't boot to sda1 at all.  It starts with the ubuntu splash screen and the progress bar goes back and forth for a few minutes before going to some kind of command prompt.

How do I get ubuntu on sda1 to boot?

---

### Post by meierfra. on 2008-05-18
I suspect that either menu.lst or fstab is using the wrong UUID.  Or ubuntu gets confused since you have two partitions with the same UUID. Please post the output of  

```
sudo blkid 
```

and

```
 sudo fdisk -l
```

Also mount your ubuntu sda1 partition (go to Places>Computer) and post the contents of  the  files "/etc/fstab" and "/boot/grub/menu.lst" from your sda1 partition. Actually  from menu.lst  just post the 

title ubuntu...
root ...
kernel ...
initrd ...

part.

---

### Post by pldobs on 2008-05-18
Output of ```
sudo blkid
```

/dev/sda1: UUID="dde12c8e-6dd8-4032-882b-19a0e155c68e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="4C5427384326FBD5" TYPE="ntfs" 
/dev/sda3: UUID="45CE-5DE4" TYPE="vfat" 
/dev/sda5: TYPE="swap" UUID="5864c159-eb4f-3492-7015-9a34f6a32525" 
/dev/sda6: UUID="dde12c8e-6dd8-4032-882b-19a0e155c68e" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="f2e3f28c-7030-4650-a771-a692d5b88d0c" 


Output of ```
sudo fdisk -l
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000530dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3354    26940973+  83  Linux
/dev/sda2            3355       11043    61761892+   7  HPFS/NTFS
/dev/sda3           11044       11172     1036192+   b  W95 FAT32
/dev/sda4           11173       14593    27479182+   5  Extended
/dev/sda5           14359       14593     1887606   82  Linux swap / Solaris
/dev/sda6           11173       14323    25310344+  83  Linux
/dev/sda7           14324       14358      281106   82  Linux swap / Solaris

output from > cat /boot/grub/menu.lst (Truncated)

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c016fdd6-1e9e-49fb-b2d4-5467ff5ef968 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot

---

### Post by meierfra. on 2008-05-18
In menu.lst replace

root=UUID=c016fdd6-1e9e-49fb-b2d4-5467ff5ef968

by 

root=/dev/sda1


Also  edit both of your /etc/fstab (on sda1 and sda6)

and replace "UUID=......" by "/dev/sda1" respectively "/dev/sda6"

---

### Post by pldobs on 2008-05-18
Did it.  Your solution worked perfectly.

Thanks much for your help.

---

