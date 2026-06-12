---
title: "Won't install on system"
date: 2016-08-04
forum: Installation &amp; Upgrades
---

### Post by legendarymedic on 2016-08-04
Hi everyone, 

First time poster, 2nd time using a Linux OS (Linux mint). I tried installing Lubuntu 14.04.4 on my Laptop (Lenovo B575 2011) and it wont install to my hard drive. I have the HDD as the 1st priority in the setup and ive installed it (no windows on this machine) but everytime I restart the pc it shows that its not on there at all. Help please. 

(code from boot repair: paste.ubuntu.com/22138267)

---

### Post by Bucky Ball on 2016-08-04
Welcome. When you boot the machine it does what exactly? Please be specific and provide details, including any error messages.

From your bootinfo, looks like you've installed Ubuntu 14.04 twice. You might consider going for 16.04 LTS as it has longer support, unless there is a reason you're not.

---

### Post by legendarymedic on 2016-08-04
Power Button: On

1) System powers up: With USB Key in (with ISO for 14.04.4 Ubuntu)
Grub 2.0 Screen -black- (Try/install/oem/check disks)

2) System Power up: Without USB key in
Intel UNDI pxe-2.1
pxe-e61 media test failure, check cable
pxe n0f exiting pxe rom

then takes me to the boot menu 
1. ATA HDD
2. ATAPI CD
3. Network Boot

EDIT: Ive tried to install Ubuntu 16 but I cant make it past the boot menu, 14.04.4 has gotten me the furthest. When I Install the OS, it says "Reboot now" and when I do, I start all over again

---

### Post by Willyweasel on 2016-08-19
> **legendarymedic said:**
> Power Button: On

2) System Power up: Without USB key in
Intel UNDI pxe-2.1
pxe-e61 media test failure, check cable
pxe n0f exiting pxe rom




I don't know if you will even see this as this post is 2 weeks old, but the quoted part from your previous reply means the computer is trying to boot from the network.
You need to change the boot priority in the bios to your hard drive.

---

