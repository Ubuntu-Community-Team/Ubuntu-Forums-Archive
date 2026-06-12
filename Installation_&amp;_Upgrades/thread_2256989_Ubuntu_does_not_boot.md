---
title: "Ubuntu does not boot"
date: 2014-12-16
forum: Installation &amp; Upgrades
---

### Post by jim79 on 2014-12-16
I have installed Ubuntu along side Windows 7 64x, but now Ubuntu will not boot. My disk has 4 partitions: sdc1(ntfs), sdc2 (ntfs), sdc5 (ext4), sdc6 (linux-swap). When I installed Ubuntu the boot loader failed "unable to install GRUB in /dev/sdb1", so I chose sdc5 instead. I have EasyBCD2.2 but when I set up Grub2 boot from sdc5 I get a GRUB4DOS screen that gives me a grub> command line and stops. Please help! Where should Ubuntu boot from? How can I get it to boot?

---

### Post by sudodus on 2014-12-16
Welcome to the Ubuntu Forums :-)

You should set up grub to boot from the head of a drive, not from a partition. It seems to me, that you want to install grub into the drive with the four partitions that you described in the opening post **/dev/sdc**

There should be no partition letter. This is how to do it during the installation.

-o-

Now I think you should try to 'repair' it, either according to this link about grub2

[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

or according to this link about Boot Repair

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

