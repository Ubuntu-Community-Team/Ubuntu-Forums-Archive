---
title: "need help with grub"
date: 2015-10-30
forum: Installation &amp; Upgrades
---

### Post by nikos_gevre on 2015-10-30
i wanted to completely format my disk which only had ubuntu installed but i failed really hard :P
the grub boot menu destroyed or something like that.
i tried different ways of restoring grub and be able to boot to ubuntu again with no success
here is the link from boot-repair [http://paste.ubuntu.com/13008835/](http://paste.ubuntu.com/13008835/)
please i need help cause the laptop is from one of my friends and not mine...

---

### Post by yancek on 2015-10-30
Your boot repair output shows you have a 1TB hard drive as well as the 8GB flash drive.  You have Grub installed to the MBR of the 1TB drive and one primary partition formatted ext3 and an Extended partition with no logical partitions.  As you can see from the boot repair output, Grub is looking for it's files on sda5 which does not exist so there is nothing to boot.

---

### Post by nikos_gevre on 2015-10-30
so what does this mean? how can i fix this?
in the end i was in a hurry so i decided to use an external program to completely wipe out my disk (a program named dban) so i think i will ok after the wipe, but i want to know how to fix the problem i mentioned above.

---

### Post by oldfred on 2015-10-30
You do not boot grub from hard drive to install. You want to go into BIOS and boot installer on flash drive. Once installed it will write a new copy of grub to MBR on hard drive for booting new install.

       [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu)

LVM or LVM with encryption is a full drive install, erases everything. That is also more advanced as LVM is logical partitions and needs different software to manage the logical partitions. If a newer user usually better to start with standard partitions and a standard install.

---

### Post by yancek on 2015-10-30
> so what does this mean? how can i fix this?

There's nothing to fix.  You formatted the partition with most of the Grub boot files so they are gone.  Since you wiped the disk, you need to reinstall as suggested above.  Use the info at the links posted above by oldfred.

---

