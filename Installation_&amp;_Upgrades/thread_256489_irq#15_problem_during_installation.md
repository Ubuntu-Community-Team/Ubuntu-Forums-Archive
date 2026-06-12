---
title: "irq#15 problem during installation"
date: 2006-09-13
forum: Installation &amp; Upgrades
---

### Post by al12345 on 2006-09-13
i cant install ubuntu becouse of a problem on ide- irq#15;
what to do?;
he says >>try to boot with the "ircpoll" option << but how to do it and if it helps i dont know;
the machine on which i am trying to instal ubuntu is think pad c30;
regards;
al;

---

### Post by jespdj on 2006-09-13
Shouldn't that be "irqpoll" instead of "ircpoll"? Look closely again.

Anyway, when you boot with the bootloader GRUB, you can add kernel parameters by highlighting the line with your Linux OS and pressing "e". Just read what the GRUB boot screen says.

Add "irqpoll" to the kernel boot parameter line.

Note, if you do it like that, you have to do it everytime you boot. If you want to make the change permanent, you'll have to edit the GRUB configuration file: /boot/grub/menu.lst

---

### Post by al12345 on 2006-09-27
i ll try this >>grub thing<<, but i am not so optimistic becouse i still dont know how to do input the >>grub<< parameter ; what i do now is to place the disk with ubuntu to the drive and switch on the power; there is no command line where i could type anything; eee:-k ; thanks for further elucidation; al

---

### Post by wpshooter on 2006-09-27
> **al12345 said:**
> i ll try this >>grub thing<<, but i am not so optimistic becouse i still dont know how to do input the >>grub<< parameter ; what i do now is to place the disk with ubuntu to the drive and switch on the power; there is no command line where i could type anything; eee:-k ; thanks for further elucidation; al

Sounds like to me that you don't actually have Ubuntu installed to your hard drive.

Why don't your try to download, burn, and install the ISO image of the ALTERNATE CD version of Dapper Drake 6.06.1.

Good luck.

---

