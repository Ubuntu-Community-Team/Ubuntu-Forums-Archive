---
title: "Kernel Panic in added old Fedora"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by chuina on 2009-12-30
hi, 

i'm using Karmic and RHEL5 with Karmic Grub.

i install one old Fedora2,in a different partition than Karmic and RHEL5. 
but failed to boot Fedora2 while RHEL5 and Karmic is still bootable. 


here is result of update-grub

```
sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found linux image: /boot/vmlinuz-2.6.18-8.el5
Found initrd image: /boot/initrd-2.6.18-8.el5.img
Found linux image: /boot/vmlinuz-2.6.5-1.358
Found initrd image: /boot/initrd-2.6.5-1.358.img
Found memtest86+ image: /memtest86+.bin
Found Red Hat Enterprise Linux Server release 5 (Tikanga) on /dev/sda3
Found Fedora Core release 2 (Tettnang) on /dev/sda4
done
```

the result of fdisk -l:

```
sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50a750a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux [/boot for all]
/dev/sda2              32        5081    40564125    5  Extended
/dev/sda3            5082        6356    10241437+  83  Linux  [RHEL5 Installed here]
/dev/sda4            6357        6993     5116702+  83  Linux [Fedora2 Installed here]
/dev/sda5              32        1247     9767488+  83  Linux [Karmic Installed here]
/dev/sda6            1248        4894    29294496   83  Linux [/home for all]
/dev/sda7            4895        5081     1502046   82  Linux swap / Solaris
```

the blkid:
```
sudo blkid 
/dev/sda3: LABEL="/" UUID="5cd1cb8c-b409-412b-921b-b425ca062b57" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: LABEL="/1" UUID="1356fab1-7a41-41f9-bc9b-a25bb62bd639" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="fae66e20-0cfb-47f2-b468-6beb9ee517a9" TYPE="swap" 
/dev/sda1: LABEL="/boot" UUID="b17b9077-d006-4c28-ba98-8e8cb239203f" TYPE="ext3" 
/dev/sda5: UUID="b3e43f43-a38c-408d-b8d7-66bec1036407" TYPE="ext3" 
/dev/sda6: LABEL="/home" UUID="c45fd77d-8dbc-498d-8aca-774c6d87133f" TYPE="ext3" 
```

*** I **attached** my grub.cfg as grub.txt

just editing the blkid for RHEL5 is fine to boot RHEL5.
But for Fedora2, Kernel Panic message gives in the first 
Screen within 5 or 6 line.

then i tried to change the blkid with /dev/sda method (i'm not sure how to write this,you'll see this in the recovery section of grub.cfg)
it load many hardwares,internel devices,CD-Rom,....
 
after 2-3 screen text message (like normal boot)
it gives like something below:

```
mount: error 6 mounting ext3
umount  /initrd/proc failed:2
Freeing unused kernel memory : 144k freed
Kernel panic : No init found . Try passing init= option to kernel
```

also, i didn't understand the "/1" in the blkid command.

Any idea/solution how to boot this old Fedora2 ?
happy new year in advance.
Thanks.

---

