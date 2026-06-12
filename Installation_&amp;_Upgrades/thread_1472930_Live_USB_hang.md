---
title: "Live USB hang"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by baddog144 on 2010-05-04
I'm trying to install 10.04 from a Live USB, but when it starts to boot, it hangs at the splash screen :(

My motherboard is a Gigabyte P55-UD3, with an i5-750.
Has anyone else run into this problem?

---

### Post by spydeyrch on 2010-05-04
What version of 10.04 are you using? x64 or x32? Also, what are some of the other specs that your system has?

CPU
HDD
RAM
GPU
ODD
Any other OSs already installed?

That will help to some extent to know your system makeup.

-Spydey :lolflag:

---

### Post by baddog144 on 2010-05-04
I'm using 32-bit 10.04. By the way, I know the USB image is ok because I just installed it on this laptop (which is very nice, by the way).

CPU: i5 750
HDD: 2 * Hitachi 500GB SATA
RAM: 4GB DDR3
GPU: ATI Radeon HD 5750
ODD: Asus... something. 

I have Windows on one of the disks, and Archlinux on the other. Is it worth unplugging them both and seeing what happens then?

---

### Post by baddog144 on 2010-05-04
Removing the hard disks didn't seem to do anything :(
EDIT: I disabled the splash screen, and now I'm getting errors related to fd0:
end_request: I/O error on fd0 sector 0
Buffered I/O error on device fd0, logical block 0

EDIT AGAIN:
Disabling the floppy in the BIOS fixed it! Installing now :D

---

### Post by spydeyrch on 2010-05-04
> **baddog144 said:**
> 
EDIT AGAIN:
Disabling the floppy in the BIOS fixed it! Installing now :D

That is strange, I don't know why disabling the floppy would do it. But good job and good luck.

-Spydey :lolflag:

---

### Post by ivlivs on 2010-08-06
> **baddog144 said:**
> Disabling the floppy in the BIOS fixed it! Installing now :D

I had the same problem on a Asus P5VD2-VM. Disabling the floppy made it work. Thank you!

---

