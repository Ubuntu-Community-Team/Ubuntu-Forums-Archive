---
title: "No bootable device"
date: 2010-06-18
forum: Installation &amp; Upgrades
---

### Post by mdewet on 2010-06-18
Hi,

I used to dual boot Windows7 RC and Ubuntu 9.04 (32bit).  Recently I deleted the W7 partition and formatted the disc for data use only, but now I can't boot into Ubuntu ('no bootable device' error on startup).  

Through the live cd using GParted I can see the Ubuntu partition being marked as 'extended', I assume because there's no MBR on there.  Is there a way that I can create a MBR on that partition or maybe change it to 'primary'?

(P.S., I dont have the 9.04 cd anymore, I downloaded the 10.04 live cd)

Thanks,
M

---

### Post by darkod on 2010-06-18
Do you have only one hdd? Was win7 on the same disk so you just deleted the ntfs partition and created a new ext4/ntfs in its place?

If yes, some BIOS don't like it when you don't have the boot flag set on a partition. Grub doesn't need the boot flag to boot correctly but BIOS might not like it without one.

Just use Gparted and put a boot flag on the primary partition you created from the win7 partition. It doesn't matter that it's not the ubuntu partition, grub2 doesn't use the flag.

See if that helps.

---

### Post by mdewet on 2010-06-18
Awesome:guitar:!

Yes setting the boot flag worked! Easy a that..

Thanks for the quick reply Darko!

---

