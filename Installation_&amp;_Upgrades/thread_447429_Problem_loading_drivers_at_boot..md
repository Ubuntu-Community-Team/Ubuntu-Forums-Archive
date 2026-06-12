---
title: "Problem loading drivers at boot."
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by Schleproque on 2007-05-18
I had to build a custom kernel for some systems and install a driver for an additional piece of hardware. Everything seems to have gone fine but the driver for the new hardware is not loading at boot. If I don't specify the complete path then I can't even load the driver by hand.

tuttle:~# insmod perle-serial
insmod: can't read 'perle-serial': No such file or directory
tuttle:~#
tuttle:~#insmod /lib/modules/2.6.12-perle/misc/perle-serial.ko
tuttle:~#

I am running 5.10 on a 386.

Thanks in adavnce.

---

### Post by trent dillman on 2007-05-18
...

---

### Post by Schleproque on 2007-05-18
> **trent dillman said:**
> sudo -i
echo "perle-serial" > /etc/modprobe.d/perle-serial
exit

The problem persists. 

Thanks.

---

### Post by Schleproque on 2007-05-18
Problem solved. 

It helps if you use the most up to date drivers.

---

