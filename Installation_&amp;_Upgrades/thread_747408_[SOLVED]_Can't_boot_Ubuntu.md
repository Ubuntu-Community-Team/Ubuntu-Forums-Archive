---
title: "[SOLVED] Can't boot Ubuntu"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by davidbessire on 2008-04-06
i'm trying to install Ubuntu 7.04 on an HP Pavilion someone gave me.  Installation process from LiveCD completes normally, but when i try to reboot several odd things happen.  Item #2 below is the main concern.

1. LiveCD ejects from DVD drive with screen message like "remove disk & press ENTER to reboot".  The keyboard is apparently disabled; pressing Enter has no effect.  Must power off at this point.

** 2. Powering back up, i cannot boot Ubuntu.  After setting the hard disk as the boot device in BIOS, i get error "disk boot failure, insert system disk & press enter".  If i insert the LiveCD, power cycle, and then select "Boot from hard disk" option from the LiveCD menu, Ubuntu starts normally.

3. Cannot shut down or reboot the system from Ubuntu desktop; system stops but remains at the shutdown screen indefinitely.

i've tried the manual grub setup described on this page to no avail:

   [http://ubuntuforums.org/archive/index.php/t-392267.html](http://ubuntuforums.org/archive/index.php/t-392267.html)

In that thread, the culprit seemed to be a faulty disk.  Although i can't rule it out, i think the disk is fine.  This is not a dual boot installation.

Any suggestions?

Thanks,
david bessire

---

### Post by Pumalite on 2008-04-06
I think you should use the Alternate CD. What are your specs?

---

### Post by davidbessire on 2008-04-06
Not sure exactly what you'd like to know...

Intel P3 850 MHz
80 GB Maxtor IDE hd
768 MB RAM
LG CD-RW
Samsung DVD-ROM

Let me know if additional information would be helpful.

Thanks for the reply
-db

---

### Post by Pumalite on 2008-04-06
I'm a little bit at a loss, but I can contribute with this. I hope it helps:
[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))
[http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/](http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/)
[http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)
[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)
[http://ubuntuforums.org/showthread.php?t=431815](http://ubuntuforums.org/showthread.php?t=431815)

---

### Post by davidbessire on 2008-04-06
Several of the pages you suggested mentioned problems with Ubuntu 7.x on HP platforms.  i installed Ubuntu 6.10 on the same machine and now have no problems whatsoever.

Thanks for your help.

-db

---

### Post by Pumalite on 2008-04-06
You are welcome. Good luck.

---

