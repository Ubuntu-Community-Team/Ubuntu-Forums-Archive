---
title: "Dual boot error"
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by daylight on 2006-09-04
after installing ubuntu 6.06 on a separate parition using the alternate.606.iso image, i encounter a "error loading operating system error" upon complete installation.

my first partition is WinXP SP2.
2nd partition is ubuntu 6.06.

no error message when installing 6.06, but i cant seem to boot properly.

although i manage to go into both OSes using the ubuntu CD.

How do i make the GRUB to load properly so that i do not have to rely on the ubuntu CD each time ?

many thanks.

---

### Post by randell6564 on 2006-09-04
> **daylight said:**
> after installing ubuntu 6.06 on a separate parition using the alternate.606.iso image, i encounter a "error loading operating system error" upon complete installation.

my first partition is WinXP SP2.
2nd partition is ubuntu 6.06.

no error message when installing 6.06, but i cant seem to boot properly.

although i manage to go into both OSes using the ubuntu CD.

How do i make the GRUB to load properly so that i do not have to rely on the ubuntu CD each time ?

many thanks.
Hi!
I got ths EXACT same problem some time ago.

Go into your Bios and choose 'LBA'.  Then reboot and see what happens.

---

### Post by daylight on 2006-09-04
did u managed to solve it ?
will try it.

btw i m using sata hdd not ide drives.

---

### Post by randell6564 on 2006-09-05
> **daylight said:**
> did u managed to solve it ?
will try it.

btw i m using sata hdd not ide drives.
HI!  On MY box, I managed to solve it by doing what i described in the previous post.

Don't know why!  I cannot give you the reason, I just know that I was having trouble dual-booting until I went into my Bios an changed from 'Auto' to 'LBA'. 

OH.,And I JUST noticed your comment about the fact that you are trying to install using a S-ATA device.

In my experience, Linux will not recognize your SATA and will install the bootloader to your Ide drive, hence the dual-boot problem!

Check out this link [http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)  

Good Luck, and PLEASE post the results of your findings!

---

### Post by daylight on 2006-09-06
no success with the LBA options.
will try dual-booting on another pata drive soon.
seems like sata drives giving me more headache

---

### Post by daylight on 2006-09-07
managed to solve the problem after i removed all my ide drives b4 installing 6.06 again.
dual boot successfully.

installed the ubuntu into my sata drive.
1st partition - WinXP (18 GB)
2nd partition - Ubuntu (40GB) and 2.6GB swap file

---

