---
title: "cannt use USB HDD with Ubuntu 7.04"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by Kumo on 2007-09-25
I install Ubuntu 7.04 finish and running before, but it cannt load Ubuntu now
The system files keep in USB HDD that I use LiveCD.

It cannt boot from Ubuntu but start WinXP anytime
How to do it ? thanks
---
my laptop suystem:
1. HDD:
&#9500;C: WinXP
&#9492;D: my files

2. USB HDD:
&#9500;E: Ubuntu
&#9492;F: my files

---

### Post by Pumalite on 2007-09-25
Set BIOS to Boot from External USB HDD.

---

### Post by Kumo on 2007-09-25
> **Pumalite said:**
> Set BIOS to Boot from External USB HDD.
Thank you

I already set USB Device before HDD, but it cannot be solved,
if I cannot find right way to solve, I only format it and reinstall again.

---

### Post by Pumalite on 2007-09-25
OK. You could use this if you want:

Re: Install on External USB Hard Drive HELP
for anyone who may wish to do exactly what i did. The easiest was that i have found is to physically disconnect all other hard drives.. Then boot from the Live CD and install on the USB hard drive using the guided partition. This was you are 100% you are only installing on the USB hard drive and the install is not trying to get space from C: drive as i found it was... Then modify you BIOS to allow for boot from usb before the internal hard drive.. Once installed reconnect any other hard drives and your good to go...

---

