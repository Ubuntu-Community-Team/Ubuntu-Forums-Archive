---
title: "Dual Boot with Windows 7 64 bit - do I need Ubuntu 64 bit?"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by monarchheels on 2010-10-17
I have an HP Slimline ADM Athlon II X2 250 Dual-Core with Windows 7 Home Premium 64-bit installed. 4GB DDR3 memory, 640 GB hard drive.

I'd like to install Ubuntu as a dual boot. **Should I use Ubuntu 32 bit or 64 bit? **

I've installed the Ubuntu 32 bit as the only OS on 3 other computers, but I've never used 64 bit, nor have I done a dual boot yet. I've read up on the dual boot installation and feel pretty ok with it, as long as I put the right version of Ubuntu on.

I'm aiming for the most trouble-free environment- it does not necessarily have to be the fastest system.

Thanks for any advice.

---

### Post by Joshwaa on 2010-10-17
I have Windows 7 64bit and Ubuntu 10.10 32bit dual boot, simply because 32bit is more supported than 64, that's all. I'd suggest using 32bit but it's your choice, 32bit is definately stable and fast enough, I've never tried 64bit but yeah, your choice, but I went with 32bit Ubuntu on a 64bit system.

---

### Post by efflandt on 2010-10-17
Grub will boot each system independently, so it does not matter from that point if you use 32 or 64-bit.  On my old PC with early Athlon64 I use to triple boot WinXP home (32-bit), 64-bit XP Pro beta, and SuSE 64-bit, and more recently same WinXP, 32-bit Ubuntu 9.10, and 64-bit 9.10 to compare (currently 64-bit 10.04).

Basic difference it that 64-bit can use all of your RAM, default 32-bit may only use 3 GB of it, but there is an optional 32-bit pae kernel that can use all of it.  But Linux requires less resources than Win7, so it will run fine even if it only uses 3 GB.

For example when 64-bit Win7 boots on my new 8 GB desktop, it seems to initially use 3.7 GB of RAM and frees up some of that later.  Or 64-bit Win7 Home Premium used 1 GB of a 4 GB laptop.  64-bit Maverick on the 8 GB (booted from USB hard drive) with nvidia drivers and Firefox running is using ~600 MB:

```
             total       used       free     shared    buffers     cached
Mem:       8121512    1032724    7088788          0      97528     322908
-/+ buffers/cache:     612288    7509224
Swap:      2152704          0    2152704
```But when I had to borrow some RAM from a Laptop 32-bit Lucid (10.04) ran fine on a laptop with 512 MB total RAM (some shared for video).

---

### Post by monarchheels on 2010-10-18
Thanks for the replies. Sounds like I'm just fine with 32 bit.
cheers

---

### Post by Csaba on 2010-11-22
A bit off topic... but:
**Why doesn't my win7 64bit show up in grub?**
I have to mention that first i've installed ubuntu 10.10 x64 and then win7 x64 but I got ubuntu working by updating grub2... however now I cannot enter into win7 anymore. (I need it for gaming like anyone else) I'm not sure what log should i look at), I'm not familiar with grub. :(
Any ideas? :)

SORRY... I've solved it.
I ran 
```
sudo update-grub2
```
again :P

---

