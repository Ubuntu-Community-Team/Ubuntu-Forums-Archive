---
title: "Making bootable system partition image?"
date: 2020-04-06
forum: Installation &amp; Upgrades
---

### Post by ander111 on 2020-04-06
Hi guys,

Can any of you tell me how I can make an image of an entire Ubuntu Mate 18.04.4  system partition, so it can be restored to a freshly formatted partition (or disk) that I can then boot from? 

I used to be able to do this with Drive Image, which booted from a DOS disk—but it doesn't support SATA drives, which I'm using now.

This being Linux, I figured there'd be all kinds of non-proprietary ways to do this, but I haven't found any yet. Thanks for your help!

---

### Post by yancek on 2020-04-06
You won't be able to boot a cloned partition as you will need boot code either in the MBR for a Legacy install or EFI files from the EFI partition for a UEFI install.  You can use clonezilla to do either a partition or an entire drive.  If you clone a partition and then clone it back to the same or a different drive, you will need some other bootloader to boot it.  You could also use the dd command to do the same and I'm sure there is other software available.

---

### Post by ander111 on 2020-05-16
> **yancek said:**
> You won't be able to boot a cloned partition as you will need boot code either in the MBR for a Legacy install or EFI files from the EFI partition for a UEFI install.  You can use clonezilla to do either a partition or an entire drive.  If you clone a partition and then clone it back to the same or a different drive, you will need some other bootloader to boot it.  You could also use the dd command to do the same and I'm sure there is other software available.

**yancek:** Thanks for your reply. I'm sorry it took over a month for me to acknowledge you. I actually posted that question for a friend here in Vancouver, BC, who was (ironically) unable to get online after an upgrade. He says:

[quote=Ander's goofy friend]
I guess you can report the thread resolved, though I had not wanted  to give a definitive response until I had a bit more experience.  As I  offered before, pleas thank them for me.

I  tried using gparted to clone my first MATE 18.04 setup before it was  blasted, and it copied but did not boot from the destination disk. In  retrospect, I may have switched destination disks for one not already  prepared with a previous Ubuntu installation, and thus lacked the GRUB  setup. I think I had previously used it with an 8.04 installation using  a much older version of GRUB.  Must try that again!

Of  course, neither Clonezilla nor gparted create compressed images like  Drive Image... I will have to investigate the compressing options on that  list you so kindly provided!

My current  MATE build is showing some odd behaviour and reporting an error to  Canonical.  There were many changes in the updates since our last try.[/quote]

So there you go. It was kind of you to help. Cheers, A.

---

