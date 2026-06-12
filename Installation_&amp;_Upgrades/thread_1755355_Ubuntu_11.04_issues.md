---
title: "Ubuntu 11.04 issues"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by Iqbal_ on 2011-05-11
Hi,
Laptop details:
64 Bits
dual boot WIndows Vista and Ubuntu 9.10. Nvidia cards, Intel core 2 duo
Three partitions 500 GB HDD for windows and four for ubuntu (/, /boot, /home and swap)
4 GB RAM
 I upgraded from ubuntu 9.10 to ubuntu 11.04. I installed ubuntu 11.04 using the boot option nomodeset, pressing F6. 

After one day the following happened.

I started ubuntu 11.04. The log-in screen came up. At that time my mobile data cable was plugged-in. The moment i clicked to enter password, the screen froze. I shutdoen by pressing power button then rebooted. Then after rebooting, I was put on (initramfs) prompt. I do not know, what to do next. I again rebooted and tried to install, using nomodeset boot option (pressing F6), the OS from LiveCD. First, the installer was taking more than usual time. Then I specified, partitions. Thereafter, it was showing saving pakages and finally it showed the message that the installer has crashed. 
If I again boot from live cd then message comes up that disk is not healthy. I can not access my home folder also using live cd. I fear my data loss.

Now is there any way out, first to back-up data and then restore the system?

---

### Post by gewin on 2011-05-11
Try booting from live cd and doing a disk check and repair with fsck on the linux partitions.

---

### Post by zvacet on 2011-05-11
You made separate home so I think all your data are there.If it is not typing mistake problem can be because you upgraded from 9.10 to 11.04 so you skipped versions with you can not do.Make clean install of Natty and during that process format /root partition and mark it as ext4.**Do not format /boot and /home partition.**Just mark them as ext4 (and whatever you use for boot) **without formating**.Of course you will use manual way to install.

---

