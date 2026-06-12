---
title: "Instal Ubuntu on a limited laptop without CD and USB"
date: 2018-05-21
forum: Installation &amp; Upgrades
---

### Post by bebs2 on 2018-05-21
Hi. First I'm sorry if there is already an answer but I've been working on my problem all day without finding one.

I own a very limited computer that for some reason, doesn't allow me to boot on USB drive. It doesn't have CD too.
It has a very small hard disk of 30 GB and came with a Windows 10 installed... at first it was enough, but Windows 10 becomes more and more greedy so it takes now 24 GB.

I already saved all my data and don't care erasing all Windows 10.

Is there a way to install Ubuntu (maybe a small one) on this ?

Regards.

EDIT:
Hardware Specifications
Brand, Model : Qilive Q8
OS : Windows 10, 32 bits
Processor : IntelAxom
RAM : 2 GB
HardDrive 30 GB

---

### Post by TheFu on 2018-05-21
2 choices:
a) You'd need to perform the install using a different PC or 
b) have a wired network connection and PXE boot support that can boot from a setup PXE boot server.

Either way, you need another machine.  For option 'a', the other machine needs to be setup enough like the first so that booting works when you pull the HDD out and swap it back into the first.  That means EFI booting if that is what it does or BIOS booting if not. Having a similar brand video card could be useful too.  Finding the exact same model would be best.

---

### Post by oldos2er on 2018-05-21
Could you please tell us the hardware specs of your computer?

---

### Post by bebs2 on 2018-05-21
> **TheFu said:**
> 2 choices:
a) You'd need to perform the install using a different PC or 
b) have a wired network connection and PXE boot support that can boot from a setup PXE boot server.

Either way, you need another machine.  For option 'a', the other machine  needs to be setup enough like the first so that booting works when you  pull the HDD out and swap it back into the first.  That means EFI  booting if that is what it does or BIOS booting if not. Having a similar  brand video card could be useful too.  Finding the exact same model  would be best.

thanks for your answer... I'll need to dome some research, because I don't really understand all this.


> **oldos2er said:**
> Could you please tell us the hardware specs of your computer?

I updated my initial post with some info. Thanks.

---

### Post by oldfred on 2018-05-21
Will it boot from the removable micro SD -SDMC card?
You may then be able to install to that. 
I have connect cards to card reader that was USB and read them, but never tried to boot from them. But Raspberry Pi uses same cards as boot device.

---

