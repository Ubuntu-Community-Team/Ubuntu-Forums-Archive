---
title: "grub error 2 when booting up external usb HD"
date: 2007-03-11
forum: Installation &amp; Upgrades
---

### Post by anson123 on 2007-03-11
Hi,

I've installed Ubuntu 6.06.1 on an external usb HD successfully, exept that when it tries to boot up, it gives me an error:

"GRUB Loading stage1.5."



"GRUB loading, please wait..."
"Error 2"


Can anyone help me with this problem?  Do I need a boot up floppy disk or something?

Thanks!

---

### Post by petteriIII on 2007-03-11
2 : "Selected disk doesn't exist"

This error is returned if the device part of a device- or full filename refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.

Comment: while your BIOS recognises USB it may be unable to boot from USB . There are many more possible reasons though.

---

### Post by anson123 on 2007-03-12
well i got it to somewhat work. i connected my external hd through sata instead of usb. however, if i turn on my hd before i turn on my computer, grub will give me an error 15. if i leave my external sata drive off and boot up my internal hd (which contains windows xp), grub will give me an error 17. HOWEVER, if i leave my external sata hd off, start up my computer, then turn on my external sata hd right before my computer scans for sata drives, then grub will work. it will come up with a menu and i can select my different kernels for ubuntu and also windows xp. if anyone knows how i can make it easier for myself, please do! if not, that's ok. thanks!

---

