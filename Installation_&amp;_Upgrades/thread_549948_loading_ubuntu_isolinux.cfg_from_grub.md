---
title: "loading ubuntu isolinux.cfg from grub"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by Lelouch on 2007-09-13
I got a tutroial of how to load puppy linux alive cd by adding a puppy option into grub menu.lst and adding puppy files into the Super Grub Disk CD...


```
title Puppy-2.16-Seamonkey-Fulldrivers
kernel $(grub_device)/vmlinuz  root=/dev/ram0 pmedia=cd
initrd $(grub_device)/initrd.gz
```

is there a way to do that with ubuntu??

---

### Post by Lelouch on 2007-09-13
he was capable of loading isolinux.cfg file of puppy linux... so i should able to load this file of ubuntu!!

---

### Post by logos34 on 2007-09-13
I think you may be referring to [this howto]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Build_a_Super_Grub_DiskGParted").

There's not enough room...the ubuntu live cd is ~697 MB...nothing left over for gparted and Super Grub.  But since the Ubuntu live cd already comes with gparted, you might be able to make a [custom ubuntu cd ]("https://help.ubuntu.com/community/LiveCDCustomization")with Super Grub added, but you'd have to take out some packages to make room.

---

