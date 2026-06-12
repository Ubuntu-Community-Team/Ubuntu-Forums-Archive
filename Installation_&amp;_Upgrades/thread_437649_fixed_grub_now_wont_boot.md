---
title: "fixed grub now wont boot"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by oddcarout on 2007-05-09
Ok,

/dev/sda1 * 1 19456 156280288+ 7 HPFS/NTFS
/dev/hda1 1 4188 33640078+ 83 Linux
/dev/hda2 4189 8159 31897057+ 83 Linux
/dev/hda3 8160 8323 1317330 82 Linux swap / Solaris
/dev/hda4 8324 9729 11293695 7 HPFS/NTFS


did this:
sudo grub
device (hd0) /dev/sda
device (hd1) /dev/hda
root (hd1,0)
setup (hd0)

now when booting Ubuntu after grub:
mounting root file system
waiting for root file system........


Please help...

---

### Post by hal8000 on 2007-05-09
Your drives dont look correct to me. Youre saying that you have a SCSI or SATA drive on IDE0 as master (sda1) for windows and also an IDE, ATA or PATA drive on IDE0 as master (hda1)

I'm sure this isnt the case, if you have two drives, can you state which is master and which is slave and which connector there using on your motherboard.

I would expect an hda an sdb or similar.

---

### Post by oddcarout on 2007-05-09
> **hal8000 said:**
> Your drives dont look correct to me. Youre saying that you have a SCSI or SATA drive on IDE0 as master (sda1) for windows and also an IDE, ATA or PATA drive on IDE0 as master (hda1)

I'm sure this isnt the case, if you have two drives, can you state which is master and which is slave and which connector there using on your motherboard.

I would expect an hda an sdb or similar.

ok I have a sata master as my windows drive
I have an eide as my linux drive

in the first post I have the out put from fdisk -l.

Thanks

---

