---
title: "Can I install without windows?"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by SoulSurvivor on 2010-05-04
Can I install the netbook remix without windows?  All the instructions talk about putting it onto a flash drive and using Windows.  Can I just use an external CD drive and install onto a new partition?  If so, will it handle all the GRUB dual-boot stuff on installation or will I have to do something special for that?

---

### Post by cuby on 2010-05-04
The installation cd is a bootable one. You can start from cd and follow the installation instructions to make a dual boot computer. Obviously you should make a backups of all important data in windows before...

---

### Post by Pauly BC on 2010-05-04
SoulSurvivor is correct that the CD is bootable. Set the BIOS to boot off the CDROM and go for it. Ubuntu should auto-detect the Windows partition and install itself onto the available empty space.

As for editing the GRUB files, follow the thread below. Ranch hand's instructions were perfect.
[http://ubuntuforums.org/showthread.php?t=1310357](http://ubuntuforums.org/showthread.php?t=1310357)

Good luck!

---

### Post by sunk8 on 2010-05-04
> **SoulSurvivor said:**
> Can I install the netbook remix without windows?  All the instructions talk about putting it onto a flash drive and using Windows.  Can I just use an external CD drive and install onto a new partition?  If so, will it handle all the GRUB dual-boot stuff on installation or will I have to do something special for that?

Yup, you can.
Boot from the CD and install on the partition of your choice.
Be careful in that step, so as to not lose data.
You might find this guide handy:
[https://wiki.ubuntu.com/ubuntu-manual](https://wiki.ubuntu.com/ubuntu-manual)

---

