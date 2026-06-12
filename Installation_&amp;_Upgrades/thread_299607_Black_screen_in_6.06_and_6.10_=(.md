---
title: "Black screen in 6.06 and 6.10 =("
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by kether on 2006-11-14
Hi everyone!
(first: sorry for my bad english >_<)

MY PC:
Atlhon 64 +3200
Video ATI radeon pro 9600 (agp)
RAM 512mb ddr
M.B. Asus A8V
HDD Sata 80GB

My problem =(
when I try to install ubuntu 6.06 or 6.10 (with previuos versions 5.10, 5.04, etc no problems), first I press F2 for select Language, next Ubuntu show me the Logo screen (loaging) and next a monitor is come Black, but a PC is ON, HDD dont work, CD-ROM dont work.. PC only ON, nothing more. I tried to press Ctrl+Alt+F1 or F2,etc (for TTY) but it doesn't happen anything. I tried to install the alternative version, all install it's OK, no problems, no errors, but when ubuntu it's loading the screen it's come black again.

please helpme =(
thank you very much!
bye!

---

### Post by MellonCollie on 2006-11-14
I had similar problems. I managed to get 6.10 to boot by going into 'recovery mode' and editing xorg.conf so that I was using the vesa driver. Then, once Ubuntu booted to the desktop, I went about installing the fglrx driver. 

(There's probably a quicker way to fix it, but that's how I did it!)

---

### Post by kether on 2006-11-14
ok, I will attempt tonight, thank you for your help! =)

---

### Post by MellonCollie on 2006-11-14
> **kether said:**
> ok, I will attempt tonight, thank you for your help! =)

Good luck!

---

### Post by kether on 2006-11-16
YES!! YES!!! IT's WORKS!! REALY THANK YOU VERY MUCH!
1 detail: don't work with normal version (ubuntu 6.10).. =( only work if you (I) install alternative version 6.10 =)

thank you again!

bye!

---

