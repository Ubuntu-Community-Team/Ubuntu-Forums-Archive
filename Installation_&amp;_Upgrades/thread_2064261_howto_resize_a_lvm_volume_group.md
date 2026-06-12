---
title: "howto resize a lvm volume group"
date: 2012-09-28
forum: Installation &amp; Upgrades
---

### Post by KisteBecks on 2012-09-28
hi,


ive setup a partition over my 80gb drive which includes a lvm volume group called vgpool but i forgot to create a boot partition outside of the lvm.
theres still space on the drive, but how do i get the volume group smaller?

inside the lvm are various logical volumes called: usr/var/home/tmp and so on.

i know that the space allocated for the volume group is bigger than all logical volumes combined.


so what i need is to shrink the volume group and after that the surrounding partition to get a small boot partition at the end of the lvm (outside of it)

a few hours ago i thought 
```

pvresize  vgpool --setphysicalvolumesize 65

```was the right command, but now im not so sure.
basically im missing vgresize - that would make the most sense.

and idea how to proceed?


the guy here used a hex editor on the partition table:
[http://www.linuxquestions.org/questions/fedora-35/how-do-i-resize-lvm-volume-group-375877/](http://www.linuxquestions.org/questions/fedora-35/how-do-i-resize-lvm-volume-group-375877/)
theres also this software from 2006: 
[http://evms.sourceforge.net](http://evms.sourceforge.net)[]("http://evms.sourceforge.net")

some infos:
```

sudo vgdisplay 
  --- Volume group ---
  VG Name               vgpool
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  14
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                7
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               70.00 GiB
  PE Size               4.00 MiB
  Total PE              17919
  Alloc PE / Size       16665 / 65.10 GiB
  Free  PE / Size       1254 / 4.90 GiB
  VG UUID               dLmEog-WIVq-e7oI-mTNq-QccA-Ds0L-z34jqq

```


```

sudo vgdisplay 
  --- Volume group ---
  VG Name               vgpool
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  14
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                7
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               70.00 GiB
  PE Size               4.00 MiB
  Total PE              17919
  Alloc PE / Size       16665 / 65.10 GiB
  Free  PE / Size       1254 / 4.90 GiB
  VG UUID               dLmEog-WIVq-e7oI-mTNq-QccA-Ds0L-z34jqq
   
julius_new@ws-wf:~$ sudo lvdisplay
  --- Logical volume ---
  LV Name                /dev/vgpool/home
  VG Name                vgpool
  LV UUID                MmAyXO-U450-dPaM-E38k-jbRQ-8LPC-imdgIp
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                40.00 GiB
  Current LE             10240
  Segments               1
  Allocation             contiguous
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Name                /dev/vgpool/boot
  VG Name                vgpool
  LV UUID                Y0YGA2-gydb-wQg1-q1IK-0xMm-QcAp-dCaE41
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                100.00 MiB
  Current LE             25
  Segments               1
  Allocation             contiguous
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
   
  --- Logical volume ---
  LV Name                /dev/vgpool/swap
  VG Name                vgpool
  LV UUID                3mcmYK-3EEM-i2Y5-5Ulh-Ht14-pRyC-nKZDqH
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                4.00 GiB
  Current LE             1024
  Segments               1
  Allocation             contiguous
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2
   
  --- Logical volume ---
  LV Name                /dev/vgpool/usr
  VG Name                vgpool
  LV UUID                lZWNol-JJfP-RMTX-9eMT-4fVm-JKzY-bVY0eB
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                6.00 GiB
  Current LE             1536
  Segments               1
  Allocation             contiguous
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:3
   
  --- Logical volume ---
  LV Name                /dev/vgpool/var
  VG Name                vgpool
  LV UUID                oMz8iq-9rPS-HOAt-DTHG-6K3O-8Nxw-w8NEtj
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                5.00 GiB
  Current LE             1280
  Segments               1
  Allocation             contiguous
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:4
   
  --- Logical volume ---
  LV Name                /dev/vgpool/root
  VG Name                vgpool
  LV UUID                peqn1h-826s-wEKz-ggXg-VoMu-GT03-bDzXPJ
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                5.00 GiB
  Current LE             1280
  Segments               1
  Allocation             contiguous
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:5
   
  --- Logical volume ---
  LV Name                /dev/vgpool/tmp
  VG Name                vgpool
  LV UUID                NATAGo-9sfG-0WMR-jgUi-1I5C-b7ow-0yDpf3
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                5.00 GiB
  Current LE             1280
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:6

```

---

### Post by darkod on 2012-09-29
Did you try running it like this first? The recent versions of ubuntu don't require the /boot partition outside the LVM like earlier.

Some LVM basics:
[http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/](http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/)

It has some reduce info among them. Just make sure you reduce the filesystem first, if you decide to do that.

---

### Post by KisteBecks on 2012-12-22
yeah, i did but not before posting....sry.

---

