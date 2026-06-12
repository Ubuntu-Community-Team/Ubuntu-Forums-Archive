---
title: "having problems installing ubuntu"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by Jameshardy88 on 2008-10-28
Hi i have installed ubuntu but when prompted to restart so that it can sort out its settings etc i am presented with this....

[34.737395] usb-storage:device scan complete
[34.738502] scsi 4:0:0:0 direct access iomega external hd pq:0 ansi:2 css
[34.743121] sd 4:0:0:0 [sbd] 1953546336 512 byte hardware sectors (1000216 mb)
[34.746008] sd 4:0:0:0 [sbd] write protect is off
[34.746078] sd 4:0:0:0 [sbd] mode sence: 00 38 00 00
[34.776151] sd 4:0:0:0 [sbd] assuming drive cache : write through
[34.750107] sd 4:0:0:0 [sbd] 1953546336 512 byte hardware sectors (1000216 mb)
[34.752982] sd 4:0:0:0 [sbd] write protect is off
[34.753049] sd 4:0:0:0 [sbd] mode sence: 00 38 00 00
[34.753125] sd 4:0:0:0 [sbd] assuming drive cache : write through
[34.753193] sdb:sbd1
[34.755288] sd 4:0:0:0 [sdb] attached scsi disk
[34.755394] sd 4:0:0:0 attached scsi generic sg2 type 0

this is using safe graphics option as the normal option would also not work and i was advised to use this option instead, i have ubuntu running on an external hard drive something i was lead to believe that i could do however it seems to me that this is what is causing the problem. Any help or opinions appreciated

thanks,

---

### Post by mikehmike on 2008-10-28
hmmm ive never tried installing onto an ext unit BUT some linux distro's are sold on USB sticks which means that linux should be bootable! 

But as you have spotted it seems a drive error!? Im not to educated with linux but im trying to learn so might as well tackle eh!

Can you explain into the graphics error that seems to be happening?


:lolflag:

---

### Post by Jameshardy88 on 2008-10-28
basically iselected ubuntu and it seemed to begin the installation (i got the ubuntu logo come up). after that i get this message...

"(initramfs) [ 51.968563] sd 4:0:0:0 [sdb] assuming drive chache :write through
[ 51.974953] sd 4:0:0:0 [sdb] assuming drive chache :write through

after which i get the flashing "_" and nothing seems to happen

i was then advised to just use the graphics boot from that point

---

### Post by mikehmike on 2008-10-28
hmmm the only thing im thinking at the moment is Read Write Permission on the Ext drive.

have you got a spare hard drive. Or even machine?

try installing Ubuntu on another HardDrive or plug the Ext HD into another machine and try installing it? :confused::confused:

:(:(

---

