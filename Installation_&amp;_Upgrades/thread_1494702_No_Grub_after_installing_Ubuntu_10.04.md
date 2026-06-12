---
title: "No Grub after installing Ubuntu 10.04"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by taekr on 2010-05-27
Hi 

I installed ubuntu 10.04 after Windows 7. 

Installing finished but no grub. It goes straight to windows 7. 

I have 3 harddisks.. 

First harddisk C: (1 TB) (SATA) 

350GB --> Windows 7
380GB --> Ubuntu 10.04
Remaining --> storage 


Second harddisk (SATA) (1TB) --> data storage.. paritioned 

Third harddisk (IDE) 350GB --> Data Storage

Hm... 

Don't know what to do.. 

Help me please

---

### Post by darkod on 2010-05-27
Grub2 was probably installed on one of the other disks. When having multiple disks it is always wise to check during the install with the Advanced button where grub2 will be installed, and make it install where you want it.

Can you run in live mode:

sudo fdisk -l

and post the results? I might be able to give you the commands to reinstall grub2 without fully running the boot info script.

---

### Post by phr33k-dc on 2010-05-27
darkod that could b what happened to me last time

---

### Post by taekr on 2010-05-27
The following is what I got


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002f252

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bb49e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91201   732572001    7  HPFS/NTFS

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe0a35e26

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       38914   312567808    7  HPFS/NTFS

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x23b523b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38245   307202931    7  HPFS/NTFS
/dev/sda2           38246       85113   376466433    5  Extended
/dev/sda3           85114      121601   293089860    7  HPFS/NTFS
/dev/sda5           38246       40677    19531250   83  Linux
/dev/sda6           40677       41175     3999744   82  Linux swap / Solaris
/dev/sda7           41175       85113   352933888   83  Linux

Disk /dev/sde: 2062 MB, 2062548992 bytes
16 heads, 32 sectors/track, 7868 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe8e3554f

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          16        7868     2010176    b  W95 FAT32

Disk /dev/sdf: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000344bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       30401   244196001    7  HPFS/NTFS

---

### Post by taekr on 2010-05-27
Any help please? 

What do I do to start Grub up?

---

### Post by taekr on 2010-05-27
Should I reinstall?

---

### Post by darkod on 2010-05-27
Nope, hold on.

You have two linux partition on /dev/sda, sda5 and sda7. sda6 is the swap partition.

Do you know if the root partition is sda5 or sda7? If it's sda5 to reinstall grub2 to /dev/sda just run from live mode:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

If root is /dev/sda7 just change the first command. The second remains the same.

Then you should see grub load when you boot.

---

### Post by taekr on 2010-05-28
Thank you very very much darkod!!!

I tried right after coming back from work. 

It works sweat!!!

---

### Post by Vishal Agarwal on 2010-05-28
Can you pls change the thread to solved !

---

