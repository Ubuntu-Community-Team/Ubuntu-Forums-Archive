---
title: "dual boot problem"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by vgopik on 2008-07-13
friends,
i am new to ubuntu.yesterday i installed ubuntu using manual partition option and installed into otherdrive rather using C to resize.after installing i restarted the system and the system doesnot show up the booting options and it automatically go to XP.how can i setup the boot options or else i need to do reinstall ubuntu using resize partition option.i need help because i am new to linux also.please let me know how to overcome this problem.
regards,
Gopi

---

### Post by WizMedic on 2008-07-14
Try the step by steps at this website:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Good luck......

---

### Post by vgopik on 2008-07-14
but i installed ubuntu on separete harddisk partition using manual partition.is there any way to get the boot sequence in this scenario or else i need to do setup again?

---

### Post by VMC on 2008-07-14
It appears you didn't set up Grub or it installed on the "other drive".

There's a couple of things to do to get you up and running. There's a program called [Super Grub]("http://www.supergrubdisk.org/") that will find you linux partitions and try to correct the situation. The download files are located on the right side of the page.

Another thing is to boot up using the Livecd and go to "Applications > Accessories > Terminal". It looks like a DOS prompt. Type the following and come back with the output:

```
sudo fdisk -l
``` (thats a lower case L)

---

