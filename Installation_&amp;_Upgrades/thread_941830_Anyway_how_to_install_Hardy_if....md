---
title: "Anyway how to install Hardy if..."
date: 2008-10-08
forum: Installation &amp; Upgrades
---

### Post by zeiz on 2008-10-08
I have Hardy. Before I had Gutsy... everything is working just fine :D.
However on my daughter's computer (that is more advanced than mine) Gutsy is running fine but Hardy even doesn't want to take a look:mad:
She has AMD64 Athlon 3000+ on Asus MB with NVidia chip, SATA HDD, 1G memory,Pioneer DVD writer.
I gave her my CD + she downloaded Hardy64 and burned CD @x4 (media check=OK, memory test=OK). Results are the same for both.
Whatever boot option we choose (install or Live) it comes to error:
[      500.406018] Buffer I/0 error on device fd0, logical block 0
[      501.903417] Buffer I/0 error on device sr0, logical block 16
[      501.909362] Buffer I/0 error on device sr0, logical block 16
[      502.060177] Buffer I/0 error on device sr0, logical block 16
[      502.066043] Buffer I/0 error on device sr0, logical block 16
[      527.374080] Buffer I/0 error on device fd0, logical block 0
[      539.420776] Buffer I/0 error on device fd0, logical block 0
.............endless:(

She has 2nd old DVD-drive and she doesn't have FDD. We disabled both in BIOS (UDMA2 option is not available for the DVDD). The result:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) _

I spent a day for research and do found similar questions however I couldn't find clear answers.
If it's really "dead" problem (hardware) may be at least anybody knows why Gutsy runs but Hardy cannot even reach install gui on the same box?:confused:

---

### Post by Kevbert on 2008-10-08
Has she performed an [[COLOR="Red"]md5sum[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") (checksum) on the ISO file that was downloaded ?

---

### Post by zeiz on 2008-10-09
she didn't (64bit) but she has also my CD that is fine (I checked) and the result is exactly the same for both. :confused:

---

### Post by overdrank on 2008-10-09
> **zeiz said:**
> she didn't (64bit) but she has also my CD that is fine (I checked) and the result is exactly the same for both. :confused:

Hi when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash and add noapic. Maybe this will help.

---

### Post by cariboo on 2008-10-10
THe installation is trying to access a floppy drive that isn't there. Have you tried setting the floppy to disabled in the BIOS?

Jim

---

