---
title: "Installing Ubuntu on Lenovo ideapad 330s"
date: 2019-10-30
forum: Installation &amp; Upgrades
---

### Post by hammundo on 2019-10-30
Hello, I have installed Ubuntu 19.10 on my Lenovo ideapad 330s and had to use the ivrs_ioapic[32]=0:14.0 and it installed on my SSD fine.

That being said I cannot boot it without my USB stick with the ISO plugged inside.

If I boot up the machine without the USB it will not load and I will get a boot menu screen and none of the options loads up Ubuntu 

I have ran a disk check and it says no errors found

Please help

Thank you
Laurence

---

### Post by ank2 on 2019-10-30
Seems the boat loader is installed on the USB stick. You need to install the boot loader on the hard disk instead.

I did this once and wrote down the info. But cannot verify if they are correct. But it will not destroy data on the USB stick nor hard drive if it fails.

Assuming your Ubuntu partition is on /dev/sda1 boot from USB. Then type

**mount /dev/sda1 /mnt****sudo grub-install --root-directory=/mnt /dev/sda**

Reboot, remove the USB stick and with some luck that sorted the problem.

---

### Post by hammundo on 2019-10-30
Hi thanks for the response.

EFI is sda1 and the file system is sda2 and when I grub install on sda2 I get a segmentation fault

---

### Post by oldfred on 2019-10-31
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by yancek on 2019-11-01
The information you posted for members to review indicates that you have a computer with ONLY Ubuntu 19.10 installed.  If that is not correct, you need to post the details of the boot repair script asked for above or we will just be guessing.

> when I grub install on sda2 I get a segmentation fault 		 

If 19.10 is your only OS, that will not work as you as you are not putting the EFI boot files on the proper partition.  Boot repair output is needed if you haven't resolved this issue.

---

