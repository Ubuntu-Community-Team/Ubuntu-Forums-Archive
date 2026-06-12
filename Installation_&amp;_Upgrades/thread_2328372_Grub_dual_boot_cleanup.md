---
title: "Grub dual boot cleanup"
date: 2016-06-20
forum: Installation &amp; Upgrades
---

### Post by Bewildered_Bob on 2016-06-20
Win 10 & Ubuntu are both loaded in "dual boot" environment but Ubu appears to be corrupted and cannot be launched so shd be completely removed. What is _***SAFEST***_ way to delete Ubu and correct (or eliminate) Grub since hopefully only Win will remain after removal. Thanx.

Newbie & Bewildered Bob

ps: live DVD is avail

---

### Post by grahammechanical on 2016-06-20
Do not delete the Linux partitions until you have restored the Windows boot loader. And I do not know how to restore the Windows boot loader as I do not use Windows. But, if I remember correctly, Boot Repair does have an option to install a generic Windows boot loader. It is under advanced options.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Regards

---

### Post by yancek on 2016-06-20
The best way to do that is to restore the windows bootloader FIRST and the method for doing that will depend on whether you are using UEFI or MBR although you generally need a windows installation DVD.  I'd suggest you do an online search or go to a windows forum.  You could also post some details about your problem with Ubuntu and someone might have a suggestion on how to resolve that.

---

