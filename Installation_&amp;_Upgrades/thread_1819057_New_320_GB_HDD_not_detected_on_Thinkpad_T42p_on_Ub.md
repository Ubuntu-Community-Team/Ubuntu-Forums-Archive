---
title: "New 320 GB HDD not detected on Thinkpad T42p on Ubuntu 11.04"
date: 2011-08-05
forum: Installation &amp; Upgrades
---

### Post by bhupi2 on 2011-08-05
My original 40 GB internal hard disk on Thinkpad T42p crashed and I bought and replaced with a new WD3200BEVE hard drive. I verified at couple of discussion forums that this drive worked with T42 without any problems. After installing, I got PXE-E61 ("Media test failure") error and the boot process halted. I took out the hard drive and replaced it making sure that it fits tightly into the slot. Now there is no PXE-E61 error and the laptop successfully boots from the Ubuntu 11.04 CDROM. However, the hard disk is not detected by the installer nor "fdisk -l" and System->Administration-> System Testing. 

Can someone suggest what might be wrong and how to proceed with installation on the new hard disk? Thanks.

---

### Post by oldfred on 2011-08-05
Welcome to the forms.

The PXE error I believe was that it could not boot from the network. Or it was booting from network before anything else per BIOS settings.

When you look in BIOS is the drive shown? Without the BIOS recognizing the drive nothing will work.

Double check that all connectors are securely plugged in.

---

### Post by bhupi2 on 2011-08-05
Thanks for the pointer. The BIOS is not recognizing the old or the new disk. I don't know why that is so, the old disk was working pretty well till few days back when I had to start using an external disk. I will try and open the laptop and check the cables as suggested by you. Thanks, again !

---

### Post by bhupi2 on 2011-08-07
I took out the drive and re- installed it,after loosening some of the screws at the back of the laptop. Then tightened the screws back. It worked. Now Ubuntu is installed on it and working much faster than my older drive! Thanks for your help, oldfred!

---

### Post by oldfred on 2011-08-07
Glad it worked.

Cannot tell you how many times I opened my desktop case and managed to loosen some connector. Many times visually they looked ok, but a push fully connected it.

---

