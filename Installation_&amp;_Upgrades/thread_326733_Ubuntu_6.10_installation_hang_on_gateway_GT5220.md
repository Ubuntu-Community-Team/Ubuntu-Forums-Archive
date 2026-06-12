---
title: "Ubuntu 6.10 installation hang on gateway GT5220"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by tcnguyen on 2006-12-28
Hi,
I am trying to install ubuntu 6.10 on this system, it's a AMD64 bit version, it runs for a minutes and hang at this stage:

[48.246240] iee1394: Initialized config rom entry `ip1394'

any idea if this version work on this system?

thanks,

-tuan

---

### Post by grizzlysmit on 2006-12-28
](*,)  I get the same problem on my Del Inspiron I get stuck in the set region/time zone then it jams up and wont procceed I think my disk is from a faulty image ](*,)

---

### Post by wpshooter on 2006-12-28
Have you checked the integrity of your CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

---

### Post by tcnguyen on 2006-12-28
yeah, I verified the image on the CD and it is fine. When I run check the disk, it hangs at the same point.

I switched to desktop live CD. It also hang after bringing up the Ubuntu graphic screen. I change the boot trap to "noapic", it went through the installation ok, however, after finishing installation and reboot, it hang again after Unbuntu graphic screen again.

This is my first time trying Ubuntu so I will continue to debug this. If anyone has a recommended solution or the version of Unbuntu that works on Gateway AMD64 bit, please let me know.

thanks,

-tuan

---

### Post by tcnguyen on 2006-12-28
well, I managed to install both live CD and alternative CD by using noapic nolapic. The installations went ok without problem. 

However, when it restart the machine, it's hung after the Ubuntu logo. Any help out there?

Any similar problem like this?

-tuan

---

