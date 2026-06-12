---
title: "Windows Recovery = Ubuntu gone"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by Microsoft Hater on 2011-01-30
Hi all,

I just reformatted my c: partition with my d: windows recovery drive, and now I lost ubuntu on sdb3. 

I used the live usb to try and see what's going on; the ext partitions still remain, and windows recognizes it's appropriate drive size. 

How do I get back into Ubuntu? There is no grub, no anything...

Any and all help is extremely appreciated.

---

### Post by matt_symes on 2011-01-30
Hi

Sounds like you need to reinstall grub. Windows overwrites the MBR.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

and read section Reinstalling from LiveCD

Kind regards

---

### Post by Microsoft Hater on 2011-01-30
That's it! Thanks very much!

---

