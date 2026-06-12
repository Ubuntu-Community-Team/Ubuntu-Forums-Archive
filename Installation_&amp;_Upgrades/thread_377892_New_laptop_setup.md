---
title: "New laptop setup"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by ethan@xmlstandards.org on 2007-03-06
Hello all,

I have just purchased a brand new VAIO laptop (VGN-FE31Z), the system specs are as follows:

Intel Core 2 Duo - 1.83GHz
2.0 Gigs of RAM
200 Gig SATA HardDisk
Wireless, Bluetooth,etc

I have been able to successfully install Ubuntu Dapper 6.06 onto this machine and have been able to get the nvidia card working correctly, however I have a simple question.

Since this is an Intel Core 2 Duo machine should I install the linux-686 kernel images instead of the linux-386 ones.

Whenever I go to the "System Monitor' under "Administration" the "Resources" tab for "CPU History" only show one processor? What gives.

I have just installed the linux-686 set of images and now I see two processors.

Which option is best for a C2D machine.

Many thanks.

---

### Post by magicfab on 2007-03-06
Actually if memory serves well, you need the linux-smp one.

The SMPT HowTo may tell you more: [http://tldp.org/HOWTO/SMP-HOWTO.html](http://tldp.org/HOWTO/SMP-HOWTO.html)

---

