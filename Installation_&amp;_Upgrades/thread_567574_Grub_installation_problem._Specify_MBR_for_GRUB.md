---
title: "Grub installation problem. Specify MBR for GRUB?"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by Schonke on 2007-10-04
A couple of months ago my system hard drive crashed and I ended up replacing my entire system except for my storage drives.

When everything had arrived and I had assembled my computer I went on installing Windows XP without any problems. When I later tried to install Ubuntu Feisty on the unpartitioned space I had left on my drive it failed to install GRUB properly.
The installation said it was completed successfully, but when I restarted the MBR on my system disk showed no signs of a GRUB installation which led me to believe that GRUB installed on a different disk's MBR.

Is there any way to specify which drive GRUB installs on when using the installer?

Thanks. :)

---

### Post by Pumalite on 2007-10-04
If you use Live CD, in step 7 of installation you have access to an 'Advanced Tab' where you can determine where you install Grub. Default is (hd0,0)

---

