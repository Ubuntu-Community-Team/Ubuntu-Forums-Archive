---
title: "Ubuntu 6.10 with SATA"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by rljacobson on 2007-01-14
I am trying to install Ubuntu 6.10 ("alternate") on a machine with the following:

Abit NF-M2S motherboard (onboard ethernet, audio, nVidia GeForce graphics)
cdrom on IDE 
Seagate Baracuda 250 GB drive (model ST3250823AS) on SATA

I get multiple "ata2:" errors immediately after selecting "text mode install" and, even if I wait a seemingly interminable amount of time, the installation ultimately fails. 

I have ruled out a faulty cdrom drive, and I get the same exact results with a similarly equipped MSI motherboard (i.e., still trying to install to SATA drive). Also, trying a different SATA drive does not help.

What can I do to get Ubuntu installed?

---

### Post by wpshooter on 2007-01-14
Are you saying that your system has only 1 SATA drive ?

If so, then are you saying that the error message is indicating that you have multiple SATA devices ?  If that is what the message is indicating you know it is wrong.

Then that makes me wonder if there is perhaps something wrong with your Ubuntu Edgy CD.

Have you checked the integrity of the Ubuntu CD by running the verfication function that is found on the initial Ubuntu boot screen menu ?

Also, have you ran the memtest function that is found on that same menu ?

---

### Post by rljacobson on 2007-01-15
Thank you for your reply. I have resolved my issue. It looks like I had a bad hard drive after all. Works like a charm now.

---

