---
title: "Server 18.04 update-grub isn't updating menu.lst"
date: 2019-02-01
forum: Installation &amp; Upgrades
---

### Post by PeterK2003 on 2019-02-01
peterk2003@Camelot:~$ sudo update-grub
[sudo] password for peterk2003:
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-44-generic
Found initrd image: /boot/initrd.img-4.15.0-44-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done


Any one know why it isn't even trying?
I did have an issue installing the 45 kernel and had to remove it...not sure if that is related?

Thanks all!

---

### Post by PeterK2003 on 2019-02-01
It appears that I was in some sort of state where grub2 was partially installed.

---

### Post by PeterK2003 on 2019-02-01
Wondering if that was why the 45 kernel version was not working.

---

### Post by yancek on 2019-02-01
What is the actual problem?  Ubuntu hasn't used Grub Legacy since version 9.04 which is almost 10 years ago.  Grub Legacy used a file named menu.lst or grub.conf, Grub2 uses the grub.cfg file which is located in the /boot/grub directory.  Your initial post output shows the update-grub command found one kernel and created a new grub.cfg file.

---

