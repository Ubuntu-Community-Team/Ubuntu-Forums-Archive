---
title: "Install trouble"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by pmccrackan on 2006-06-14
Hi, I am attempting to install Ubuntu64 onto my system. I wish to dual boot with XP.
I have 2 * 80 GB sata hard drives. There is some 80 Gb of unallocated space in total on the system (largest chunk is 57GB unallocated)
I will be installing onto my unallocated space.
when I insert the cd and boot up I select the run or install unbuntu option, it then loads essential drivers, Mounting Root file system takes a few minutes maybe around 3.
Decompressing Linux... Done
Booting the kernel...
[ 178.518122 ] hda: ide_intr: huh? expected NULL handler on exit. (this happens 2 times at a differnet [address] and then I ge this)
197.839313 Buffer I/O error on device hda, logical block 377836 (then the "huh?" bit happens again)
And so it cycles on through these error messages, I have no idea how long it would continue to go on.
I did a search for the error message sbut did not get anything really useful.
Appreciate it if someone could help me out.
Cheers, Peter.

---

### Post by elbryan on 2006-06-14
It's quite strange...

```

[ 178.518122 ] hda: ide_intr: huh? expected NULL handler on exit. (this happens 2 times at a differnet [address] and then I ge this)
197.839313 Buffer I/O error on device hda, logical block 377836 (then the "huh?" bit happens again)

```

I have 2 sata hdd as well but Kubuntu recognize them as SCSI driver .. (sda and sdb).

Try to go into the bios and set into IDE Configuration the Compatible Mode for your devices and retry ..

---

