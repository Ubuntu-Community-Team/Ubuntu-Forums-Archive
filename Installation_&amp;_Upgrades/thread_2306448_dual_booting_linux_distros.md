---
title: "dual booting linux distros"
date: 2015-12-15
forum: Installation &amp; Upgrades
---

### Post by HappyAsHellas on 2015-12-15
I used to dual boot with windows 10 and Ubuntu, before wiping out windows altogether. Can I dual boot with different versions of linux? I am very happy with Ubuntu but with so many other versions available I quite fancy comparing my present set up with, say linux mint. Any suggestions anyone.

---

### Post by ian-weisser on 2015-12-15
> **HappyAsHellas said:**
> Can I dual boot with different versions of linux?

Yes you can multi-boot, and the process is generally much easier if Windows or OSX isn't one of them.
Start at [https://help.ubuntu.com/community/DualBoot](https://help.ubuntu.com/community/DualBoot)

Alternately, you can use a Virtual Machine to try out a new distro without repartitioning your disk(s).
Several good VMs are available free in Ubuntu's Software Center.

---

### Post by grahammechanical on 2015-12-15
Keep this in mind:

The last Linux to be installed will install its Grub into the MBR of the hard disk and this will put the last Linux installed in charge of the boot loader menu. We can quickly get confused as to which boot menu we are loading from. If we then delete the Linux that is in charge of the boot loader we will have a broken boot loader.

So, decide in advance which Linux is to be in charge of the boot loader. For example, Ubuntu. Then after each install of a Linux version load into Ubuntu and run

```
sudo update-grub
sudo grub-install /dev/sda
```

Assuming that there is only one hard disk. That will also keep Ubuntu in charge of the boot menu and we can then delete the other Linux versions if we should wish and still load into Ubuntu and then run the commands again to clean up the boot menu.

Regards.

---

### Post by yancek on 2015-12-15
You can install and boot Linux systems from an internal hard drive, and external usb drive or flash drive.  The number of distributions is basically limited only by the size of your drive(s).  You will need to inform yourself on the Grub bootloader.

---

### Post by sudodus on 2015-12-16
It is simple and does not interfere with your internal drive, if you try the other linux distros live, persistent live, or installed into an ***external drive, for example a fast USB 3 pendrive***. Installing into an external drive is like installing into an internal drive, but you should use **Something else** at the partitioning window of the installer and make sure that the bootloader is installed into the external drive. Otherwise it will hi-jack the boot-loading of the internal drive.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by HappyAsHellas on 2015-12-16
Many thanks for all your help

---

