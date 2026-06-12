---
title: "ub7.0.4 ICH5R chipset with SATA drives troubles"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by M.Verkerk on 2007-08-07
Hi everyone!

I experienced some troubles with the hard drive on my system. First, during the installation using either 7.0.4 normal or alternate, it takes a very long while to detect my hard drives, but in the end they detect well. When I have set the preferred partioning scheme, it again takes a very long while. 

After that the system installs well, but when I try to start-up afterwards, the system gives a message on that the root drive hasn't been checked for a strange number of mounts and checking fails afterwards.

This is a new installation and my drives where detected well with previous version of Ubuntu!

Any suggestions?


Kind regards,
Marijn

---

### Post by Pumalite on 2007-08-07
Post your specs; including RAM and video card.
Post fdisk -l (small L )( or equivalent)

---

### Post by M.Verkerk on 2007-08-08
The harddrive isn't automatically detected, but after running gparted or after loading the appropriate kernel module fdisk gives the following output:

Fdisk:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       19457    53890042+   5  Extended
/dev/sda5           12749       19457    53890011    b  W95 FAT32

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS
```

Further, this is a:

P4 3000 Mhz
asus p4p-deluxe mb
1024 mb ram
nvidea gforce fx 5900 deluxe (256 mb)

Thanks in advance!

Marijn

---

### Post by M.Verkerk on 2007-08-08
BTW, I managed to partition /dev/sdb under linux, but I had to repartition it NTFS to check the harddrive under windows for hardware  errors.

---

### Post by Pumalite on 2007-08-08
What was the result of chkdsk? Did you do it on both drives? If the result was: OK; then my advice is: re-install.

---

### Post by M.Verkerk on 2007-08-08
I had to setup the NTFS partition to use some hardware specific tools to check my hardrive, read, write checks and a write-zero check, all succeeded..

I have installed Ubuntu 6.0.6 previously, without problems, removed it a while a go and now I have tried to install 7.0.4 two times, but with the hardrive problems. Since I installed it previously, I thought that my hardrive was broken, but now I know that isn't the case. Could it be some kernel problem?

BTW, I only checked the 2nd drive.. The first drive is running Windows XP.

Marijn

---

### Post by Pumalite on 2007-08-08
If you are planning to install Grub to the MBR, you should check the 1st drive too. Check you BIOS too. Make sure your IDE's are set to 'Auto'.

---

### Post by M.Verkerk on 2007-08-08
Thanks, but grub worked fine!

---

