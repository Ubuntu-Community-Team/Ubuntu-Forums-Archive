---
title: "Installer failing to mount CD"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by s_e_t_y on 2008-08-05
Hi,

I've got *Ubuntu 8.04 LTS Server Edition*. 
I booted from CD and selected the option to install.
It loaded the kernel and started the installer, which is then failing to mount the CD.

The installer has an option to start the konsole, allowing to mount the CD manually. But i couldn't find the device file to mount.
RedHat uses /dev/cdrom, not sure what ubuntu uses. (it's a standard parallel bus Asus CD writer).

Any idea why it's failing to mount?:confused:
Or at least, what's the device file for CD drive in ubuntu?

Thanks for your time,
Sety.:)

---

### Post by JimGvo on 2008-08-05
Is this perchance a P965 chipset motherboard?  What motherboard?  Have you been able to install anything on this system before?

Jim.

---

### Post by dstew on 2008-08-05
It could be that the installation CD's driver is having trouble running your CD ROM drive. This can happen especially with IDE-interface CD-ROM drives. Sometimes, the problem is your drive is not being auto-detected. Make sure if it is the only drive on its interface that it is jumpered as Master. If you know what drive number it is, you can add a kernel parameter to the installatiion CD kernel line to tell the driver exactly where the CD-ROM is. For example, if you think the CD-ROM is the second IDE device, you can add the kernel parameter **hdb=cdrom**. You press F6 at the opening menu to add kernel parameters.

You should also look at any system error messages to try to figure out exaclty why the CD-ROM is not being mounted. After the error, do you get the option to open a command line? If so, you can try the **dmesg** command.

---

