---
title: "Boot stops on EXT4-fs (sda8): internal journal on sda8:8"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dude2425 on 2009-10-18
I rebooted last night and the boot process seemed to stop, so I rebooted into recovery mode and the last message displayed was 

EXT4-fs (sda8): internal journal on sda8:8

and nothing happens after that. I can boot to live usb just fine for troubleshooting purposes. I did a full update/upgrade via a chroot in live usb to no avail. This happens on my customized kernel and also the Ubuntu kernels.

I fixed the problem with much help from #ubuntu+1 on freenode. My swap partition is corrupt or something and somehow it got uncommented from /etc/fstab. I dunno why I uncommented it there, but it doesn't bother me right now.

---

