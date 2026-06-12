---
title: "How to boot live cd in vesa mode ?"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by chrissk_2 on 2010-09-29
Hello,

i want to boot the live cd of ubuntu 10.10 in safe mode (vesa or fbdev driver). The boot options are gone. Is there any way to show them ?
The pc freezes before the first boot image shows (its like it freezes before the bootloader).

I have an imac with 7600 nvidia but the graphic card is fried. I use ubuntu 10.04 with software rendering but no 3d hardware acceleration. 
Because of the broken card nouveau KMS fails so i can only boot with fbdev or vesa which is fine with me

Any help is appreciated

---

### Post by Rubi1200 on 2010-09-29
When Ubuntu starts:

F6 then Esc to see the boot:

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

Remove quiet splash and add xforcevesa so it looks like this


**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz xforcevesa --**

Then Enter to boot.

---

### Post by chrissk_2 on 2010-09-30
Yes but i don't reach that point. It freezes before it shows anything. Fedora shows the boot screen (with the 10 secs countdown) and there i can select safe mode. In ubuntu it does not reach that point. Any thoughts ?

---

### Post by chrissk_2 on 2010-10-09
Ok after some more searching i found that it needed the special live cd from ubuntu for mac. Probably some EFI issue

---

