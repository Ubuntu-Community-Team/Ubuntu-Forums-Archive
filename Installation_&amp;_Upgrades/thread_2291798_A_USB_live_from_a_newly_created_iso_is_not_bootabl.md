---
title: "A USB live from a newly created iso is not bootable (but works on VirtualBox!)"
date: 2015-08-22
forum: Installation &amp; Upgrades
---

### Post by febrezo on 2015-08-22
Hi there,

I have created a custom ISO of an elementary OS (based on Ubuntu 14.04 Trusty) which works (runs the trial and gets installed)in a Virtual Box environment. However, when trying to copy it to two different USB (unmounted), it does not work.

>  sudo dd if=mynewdistro.iso of=/dev/sdb

The command ends without errors. When plugged on two different computers with USB boot activated (and tested) the system does not recognize it as a bootable device and starts the hosted HDD OS (Windows 7 and elementary). I have confirmed that the dd command is OK as I have burnt a fresh elementary OS disk on the USBand got it working in the VM machines and in the physical systems.

I need help to try to troubleshoot the problem since I am not sure how to go on with my tests. The point is that this has made me lose confidence when trying my new system on Virtual Box (23 tested on VBox alpha versions) as I am no longer sure if the system will really work when being copied to a USB.

---

### Post by yancek on 2015-08-22
I believe if you are using dd you need to make the iso a hybrid.  Simple command shown at the link below and more details at the second link.  The major Linux distribution iso files you download are almost all hybrid.

[http://superuser.com/questions/591234/creating-a-bootable-usb-from-command-line-on-linux/592656#592656](http://superuser.com/questions/591234/creating-a-bootable-usb-from-command-line-on-linux/592656#592656)

[http://www.syslinux.org/wiki/index.php/Doc/isolinux#HYBRID_CD-ROM.2FHARD_DISK_MODE](http://www.syslinux.org/wiki/index.php/Doc/isolinux#HYBRID_CD-ROM.2FHARD_DISK_MODE)

---

### Post by febrezo on 2015-08-23
Thanks Yancek. isohybrid did the rest. With the links I read, it makes sense the fact of VBox reading the ISO as it was mounted as a CD/DVD but i was copying it to a USB which needed to make it hybrid. I'll copy the full (and straight-forward) solution:
> # After creating the iso, making it hybrid
sudo isohybrid mynewiso.iso
# This threw my a warning but worked anyway:
#isohybrid: Warning: more than 1024 cylinders: 2243
#isohybrid: Not all BIOSes will be able to boot this device

# DD-ing it to the USB
sudo dd if=mynewiso.iso of=/dev/sdX bs=4k # In my case, this was sdb so: sudo dd if=mynewiso.iso of=/dev/sdb bs=4k

Marking this as solved.

---

