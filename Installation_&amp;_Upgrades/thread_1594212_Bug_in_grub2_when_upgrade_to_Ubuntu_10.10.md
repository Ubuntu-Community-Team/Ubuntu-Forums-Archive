---
title: "Bug in grub2 when upgrade to Ubuntu 10.10"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by Hyvi on 2010-10-12
I have upgrade from ubuntu 10.4 to ubuntu 10.10, it succed .

but today ,i run into a problem ..

when i run in terminal 
> sudo update-grub
and the note as follow :
```

hyvi@hyvi-laptop:/$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 10.04.1 LTS (10.04) on /dev/sda1
done

```
I have upgrade to ubuntu10.10 ,but it only found the 10.04.1.
it is a bug of grub2 ?

---

### Post by arubislander on 2010-10-12
I don't think it is a grub2 bug. More likely you had two installs of Ubuntu 10.04.1 LTS side by side. You upgraded the one, and the other is still at 10.04.1.

Could you post the results of ```
$ sudo fdisk -l
```

That last character is a lower case L, not a number one.

---

### Post by Hyvi on 2010-10-12
> **arubislander said:**
> I don't think it is a grub2 bug. More likely you had two installs of Ubuntu 10.04.1 LTS side by side. You upgraded the one, and the other is still at 10.04.1.

Could you post the results of ```
$ sudo fdisk -l
```That last character is a lower case L, not a number one.
thank you for your reply
it is ..
run ```
sudo fdisk -l
```
as follows: 
> hyvi@hyvi-laptop:/$ sudo fdisk -l
[sudo] password for hyvi: 

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7f0ff005

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3769    30271488   83  Linux
/dev/sda2            3769       19453   125975553    5  Extended
/dev/sda5            3769       19210   124022784   83  Linux
/dev/sda6           19210       19453     1951744   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9c9e0dc6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1909    15330304   83  Linux
/dev/sdb2            1909        3649    13977600    7  HPFS/NTFS
/dev/sdb3            3649       10522    55208960    7  HPFS/NTFS
/dev/sdb4           10522       19458    71772160    f  W95 Ext'd (LBA)
/dev/sdb5           10522       13134    20973536+   7  HPFS/NTFS
/dev/sdb6           13134       15745    20973536+   7  HPFS/NTFS
/dev/sdb7           15745       19458    29824992+   7  HPFS/NTFS


I am now in ubuntu 10.10 in /dev/sdb1, **grub2** found the other ubuntu 10.04 in /dev/sda1 .

---

### Post by garvinrick4 on 2010-10-12
sda1 is linux   30 gig
sda5 is linux 124 gig
sda6 is  2 gig of swap

sdb1 is linux   15 gig

and 2.6.35-22 in sda5 is 10.10 maverick
and sda1 is 10.04 lucid
and sdb1 ?

All seems to be working so you got an extra.

---

### Post by Hyvi on 2010-10-12
> **garvinrick4 said:**
> sda1 is linux   30 gig
sda5 is linux 124 gig
sda6 is  2 gig of swap

sdb1 is linux   15 gig

and 2.6.35-22 in sda5 is 10.10 maverick
and sda1 is 10.04 lucid
and sdb1 ?

All seems to be working so you got an extra.

 
2.6.35-22 in  sdb1 is 10.10 maverick. and 2.6.32-25 is kernel of 10.04 lucid , also in sdb1. 

you can understand after you see my grub.cfg in the folder of  "/boot/grub/" . as follows:
```
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod part_msdos
        insmod ext2
        set root='(hd1,msdos1)'
        search --no-floppy --fs-uuid --set 713f5125-d266-4068-993e-817d91f84155
        linux   /boot/vmlinuz-2.6.35-22-generic root=UUID=713f5125-d266-4068-993e-817d91f84155 ro   quiet splash
        initrd  /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod part_msdos
        insmod ext2
        set root='(hd1,msdos1)'
        search --no-floppy --fs-uuid --set 713f5125-d266-4068-993e-817d91f84155
        echo    'Loading Linux 2.6.35-22-generic ...'
        linux   /boot/vmlinuz-2.6.35-22-generic root=UUID=713f5125-d266-4068-993e-817d91f84155 ro single 
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod part_msdos
        insmod ext2
        set root='(hd1,msdos1)'
        search --no-floppy --fs-uuid --set 713f5125-d266-4068-993e-817d91f84155
        linux   /boot/vmlinuz-2.6.32-25-generic root=UUID=713f5125-d266-4068-993e-817d91f84155 ro   quiet splash
        initrd  /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod part_msdos
        insmod ext2
        set root='(hd1,msdos1)'
        search --no-floppy --fs-uuid --set 713f5125-d266-4068-993e-817d91f84155
        echo    'Loading Linux 2.6.32-25-generic ...'
        linux   /boot/vmlinuz-2.6.32-25-generic root=UUID=713f5125-d266-4068-993e-817d91f84155 ro single 
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-2.6.32-25-generic
}

```

and  ubuntu 10.04  is in sda1 .

---

### Post by arubislander on 2010-10-12
So it's all clear now? If so please mark this thread as solved.

---

### Post by Hyvi on 2010-10-12
> **arubislander said:**
> So it's all clear now? If so please mark this thread as solved.
Thanks for your Remind.
I has marked. I want to ask about thread modes ,what does "Hybird mode" and "threaded mode " mean

---

