---
title: "initramfs error in Ubuntu 8.10"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by ipskhurana on 2008-11-28
hi

at present i am using ubuntu 8.04 which is working fine except for a sound,

now i had tried to celan install Ubuntu 8.10, but when install starts it show error "initramfs" in terminal and does not goes further.

i am using P3 Asus bx440 mbd, Intel Cpu 550 mhz, 512 mb sd ram and 80 gb ide hdd.

Asus bx440 does not supports sata (in bios).
i.e i am using ide 80gb hdd

but i want to install ubuntu 8.10, what should i do.

i also tried following as suggested in Orkut Ubuntu Forums

"
Boot from CD. Select language, now press F6 for advanced boot options. Something like this will appear:

Boot Options file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --

Remove "quiet splash --" and replace that with all_generic_ide
Press Enter to boot and start installation.
"

also

"all_generic_ide root=/dev/cdrom
"

but still showing same

"kjournald starting commit interval 5 seconds
Ext3-fs mounted filesystem with datamode"

this msg shows goes on for 106 times...

what to do?
i want to install it any how !

pls confirm in detail.

Thanks n Rgds
Inder

---

