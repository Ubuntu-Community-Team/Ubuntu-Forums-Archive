---
title: "New Hardware, Installer not seeing internal hard drive"
date: 2010-09-26
forum: Installation &amp; Upgrades
---

### Post by mattgaunt on 2010-09-26
Hey everyone,

I've just put together a new machine and as I expected, there are some issues with hardware :-P

I've just tried to set up the installation of ubuntu, got to the partitioning section and only my external hard drive is being picked up. The internal hard drive is a 1TB SATA drive plugged into a 6GB/s DATA port on my m/b (Gigabyte GA-P55A-UD4 running Intel i5 760 processor).

I'm probably going to try the alternate CD to see if that works, but does anyone know if this is a common problem for any of my hardware? (I did a google but couldn't find anything)

Cheers,
Matt

---

### Post by cascade9 on 2010-09-26
Ahh, this old problem again. 

You've hooked up to the Marvel 9128 SATAIII controller? Disconnect it, and hook the HDD up to the Intel SATAII controller. The Intel controller should work fine.

You migth be able to get the 9128 going if you've set it to ACHI mode in BIOS, but really, the marvel controllers are so bad you are better of with the intel controller anyway. Its not like SATAIII is going to give you any real advatanges over SATAII with a mechanical HDD.

---

### Post by mattgaunt on 2010-09-26
Cheers Cascade9, you were spot on.

Swapped over the sata and everything worked as expected :-)

---

### Post by cascade9 on 2010-09-26
Excelent, glad it worked. 

Enjoy your new system ;)

---

