---
title: "Intel Controler + Ubuntu: Problems and Problems"
date: 2005-09-08
forum: Installation &amp; Upgrades
---

### Post by Marcelo Santos on 2005-09-08
Hi Guys,

When I try to install Ubuntu, in console I see this message:

IRQ18: nobody cared (try booting with the "irqpoll" option)
handlers:
[<f8877e24>] ......idecore
[<f8877e24>] ......idecore
[<f8877e24>] ......usbcore
Disabling IRQ18

And, the process to mount the CD and copy files to disk is very slow. About 3 hours...

My system:

Pentium4 HT
Asus P4P800-E Deluxe (Intel 865)
2 x Seagate SATA HD 160 GB (ntfs)
1 x Maxtor 120 GB (old C:, winxp System)

The Ubuntu System will be instaled on Maxtor disk, disk0.

I really don't know whats is wrong. 

Any help would be very appreciated.

Marcelo.

---

### Post by Marcelo Santos on 2005-09-08
The Problem was solved.

Enter in bios and disable enhanced performance for Paralel ATA Hard Disk (only on SATA device).

I'm using (and posting) from Ubuntu System...  \\:D/ 

Marcelo.

---

