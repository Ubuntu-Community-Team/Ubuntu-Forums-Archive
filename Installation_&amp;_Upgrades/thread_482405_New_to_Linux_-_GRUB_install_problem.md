---
title: "New to Linux - GRUB install problem"
date: 2007-06-23
forum: Installation &amp; Upgrades
---

### Post by cc3055 on 2007-06-23
Hello,

I used the alt installation disk. for 7.04 verion

I have a 40 gig internal hd on my laptop
I have a 160 gig on my Firewire HD
I have a 80 gig USB HD where Linux was installed to:

Here is the partition info on the 80 gig HD.  I let Ubuntu decided how to partition the HD

SCSI 4 (0,0,0) sdc 80 gig
#2 Prim 18 gig  ext3  /
#5 Logical 764.9MB Swap
#1 Primary 61.3GB f32

When i boot the USB HD GRUB come up on the screen, i select the first choice which is Ubuntu, i hit the enter key and i get an error message 12.  I think it was 12.

I typed "e" to edit the boot line it is showing hd1 and not sdc.

I don't know how to point it to the sdc drive.

I hope i have given enough info.

Thanks, CC

---

### Post by logos34 on 2007-06-23
One thing is clear: sdc is your 80gb linux drive, and at the time of install was designated '(hd1)', or the second drive detected in the bios, but it seems to have changed since then.  If you're sure you are booting directly to the grub menu on the USB drive--and not the internal drive--then you could try 'e' to edit the 'root' line to 'root (hd0,1)'--i.e. /dev/sdc2.  Hit enter after the change and 'b' to boot.  The reason for changing to is that whatever drive you put first in the bios hard disk boot order becomes (hd0).  If you're able to boot into linux make the change permanent by editing menu.lst.  

If not you'll need to execute a shell on /dev/sdc2 in rescue mode on the alt install cd and get to your files /boot/grub/menu.lst and device.map to edit them.

---

### Post by cc3055 on 2007-06-27
Thank you so much. It worked.

I am excited about using Ubuntu :p

-cc

---

### Post by logos34 on 2007-06-28
> **cc3055 said:**
> Thank you so much. It worked.

I am excited about using Ubuntu :p

-cc

glad to hear that.

enjoy!

---

