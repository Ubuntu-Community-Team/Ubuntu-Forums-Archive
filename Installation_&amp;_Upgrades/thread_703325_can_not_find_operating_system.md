---
title: "can not find operating system"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by fattysfinest on 2008-02-21
hi, I finally took the plunge and installed gutsy on my home pc. Duel boot with xp.
I cant get past the bios screen? when i get the no os screen then nothing. Heres what sudo fdisk -lu gives me. any help as always is greatly appreciated.
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb4d6b4d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   296222534   148111236    7  HPFS/NTFS
/dev/sda2   *   296222535   484199099    93988282+  83  Linux
/dev/sda3       484199100   490223474     3012187+   5  Extended
/dev/sda5       484199163   490223474     3012156   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by renzokuken on 2008-02-21
you could use a SuperGrubCD to boot into whichever operating system, then from linux you could try reinstalling grub

---

### Post by fattysfinest on 2008-02-21
thanks for your suggestion, I have tried the super grub and when i try to fix the grub for linux I keep getting a "error 15,File not found.
If i try to fix windoze it gives my the check disc screen but wont reboot to anything.
Any thoughts?
I can now use xp, I still get the file not found error.
Is it possible my  Gutsy install didn't work and I need to reload it? if so how do I make sure that I install it in the correct partition?

---

