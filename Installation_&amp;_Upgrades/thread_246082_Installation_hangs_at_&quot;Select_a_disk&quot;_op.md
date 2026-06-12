---
title: "Installation hangs at &quot;Select a disk&quot; option"
date: 2006-08-28
forum: Installation &amp; Upgrades
---

### Post by ryaowe on 2006-08-28
I've searched the forums and found similar postings, but haven't found anything that works for me yet.

After the installer initializes the partitioning tool, it goes to a dialog saying "Select a disk...", and then has an a busy cursor that never seems to finish.

My hardware is as follows:
ASUS A8V-MX Micro-ATX motherboard
AMD 3800+ X2 CPU
WD320GB SATA 3.0Gb/s HDD
IDE DVD/RW

Maybe its the fact that I have an IDE DVD drive and a SATA HDD??
I've tried all the different BIOS settings for the SATA drive, with no difference.

I'm using the x86 installer even though the CPU is x86_64, could that be a problem?

Thanks in advance for any help!!

---

### Post by ryaowe on 2006-08-29
So, if I use the alternate install CD, then I can partition the drive and get to the base installation.  Unfortunately, at that point it fails, saying that bsdutils_2.12r-4ubuntu6_i386.deb is corrupt.  But when I run the "Check CD for Defects" from the boot menu, it says that the CD is fine...

Is this package one that is installed from the CD, or is it downloaded at install time?

I can continue the installation after the error, but there are several other packages that depend on bsdutils, so the installation eventually fails.

Any ideas?

---

### Post by L_o_N_e_R on 2006-08-29
i used to have this prob also with the live cd.....

my solution? exit all progs that are runnuing(exept the isntaler)

---

### Post by wpshooter on 2006-08-29
> **L_o_N_e_R said:**
> i used to have this prob also with the live cd.....

my solution? exit all progs that are runnuing(exept the isntaler)

May I ask why and what other programs you would be running if you were doing an O/S installation ?

Thanks.

---

### Post by etcpool on 2006-08-29
for dapper latest installer cd

the installer is just like a program running on your os

you can browse the internet chating with your friends via the im and all other things with the programs included in the live cd , while you are installing your dapper ...

---

### Post by wpshooter on 2006-08-30
> **etcpool said:**
> for dapper latest installer cd

the installer is just like a program running on your os

you can browse the internet chating with your friends via the im and all other things with the programs included in the live cd , while you are installing your dapper ...

I am sure you **CAN** do all of this, but I don't think it would be advisable !!!

---

