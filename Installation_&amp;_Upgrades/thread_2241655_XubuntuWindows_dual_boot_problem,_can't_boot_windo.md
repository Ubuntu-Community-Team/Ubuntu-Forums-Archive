---
title: "Xubuntu/Windows dual boot problem, can't boot windows"
date: 2014-08-27
forum: Installation &amp; Upgrades
---

### Post by Do_Dorito on 2014-08-27
The windows option isn't even on grub, there is only a "Recover Windows files (loader)" option which loads files for a bit, and then just restarts the computer.
I tried fixing it with Boot Repair, but nothing changed.
Here is the link boot repair gave me: [http://paste.ubuntu.com/8161200](http://paste.ubuntu.com/8161200)

---

### Post by yancek on 2014-08-27
I'm not sure what the problem is but I see you have FreeDOS on sda1, your windows (7 or 8?) on sda2 and the Recovery on sda3 with Ubuntu also installed.  I would start by booting Ubuntu and running sudo os-prober and see if you get any output indicating sda2.  I don't know if Boot Repair is supposed to do this.  If you see anything indicating sda2, run:  sudo update-grub and again watch the output and reboot.

Have you been able to boot windows since installing FreeDOS?

---

### Post by Do_Dorito on 2014-08-27
Ok, i ran os-prober and got this
/dev/sda1:FreeDOS:FreeDOS:chain
/dev/sda3:Windows Recovery Environment (loader):Windows:chain

also when i ran update-grub it found only sda1 and 3(and linux and memtest images)
edit: update-grub output:
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found FreeDOS on /dev/sda1
Found Windows Recovery Environment (loader) on /dev/sda3

edit 2:
this laptop came with free dos, and i installed and used windows afterwards

---

