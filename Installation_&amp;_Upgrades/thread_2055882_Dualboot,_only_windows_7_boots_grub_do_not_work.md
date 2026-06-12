---
title: "Dualboot, only windows 7 boots grub do not work"
date: 2012-09-10
forum: Installation &amp; Upgrades
---

### Post by kimnilsson on 2012-09-10
Hello,

I have some trouble with dualboot on my machine. Hasn't used windows for a couple of years but need it installed now, and an virtual machine isn't god enough sadly. 

The problem is the following:
Windows boots perfectly.
If I remove the windows disc  and try to boot from the Ubuntu installation Grub gets an error message.
"*error: invalid arch independent ELF magic*".
When I install ubuntu alongside windows I tested to write grud on both sda, sdb and on windows 7 bootloader.
Same error on all three configurations.
Then I tried to use windows bootloader for loading Ubuntu and I get the same error message as earlier.:(
Configuration:
Harddisk is following 120Gb Intel 330 SSD -- 60Gb Intel 330 SSD -- Seageate 320gb for data storage.
Windows is installed on the 120gb SSD and is connected on SATA1 and first in bootorder.
Ubuntu is on the 60Gb SSD and on SATA2 and second in bootloader.

I would be really happy if someone could explain or help me with this problem. :)

---

### Post by darkod on 2012-09-10
If grub2 is not on the 120GB why would it be first in the boot order?

You need the disk where grub2 is installed to be the first in the boot order since the windows bootloader can't boot ubuntu.

If you don't know what is where, boot into live mode with the ubuntu cd and in terminal run:
```
sudo parted -l (small L)
```

Post the output.

---

