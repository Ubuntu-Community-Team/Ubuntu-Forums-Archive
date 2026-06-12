---
title: "Ubuntu booting to grub prompt on external hdd"
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by pemmarajut on 2010-08-02
I have a PC with no hard drive so I installed Ubuntu 10.04 on an external (1TB) hard drive using a 4GB flash drive as the install medium. The installation was successful (although formatting the drive as EXT4 to a loooong time).  When I rebooted, the grub recovery prompt came up instead of the grub menu saying error:file not found.

Now every time I boot, I have to type in these commands:
set root=(hd0,1)
linux /boot/vmlinuz-x.x.xx-xx-generic root=/dev/sda1 ro
initrd /boot/initrd.img-x.x.xx-xx-generic
boot

After boot, if I try to reinstall grub, there is no difference and the same recovery prompt comes up. Do any of you guys have any suggestions?

---

### Post by dino99 on 2010-08-02
is your external drive always plugged ? The problem with external drive plugged/unplugged is that uuid can change, so the solution is to give it a label, then use this label instead of uuid

[http://www.linuxquestions.org/questions/linux-software-2/using-labels-in-grub2-how-819474/](http://www.linuxquestions.org/questions/linux-software-2/using-labels-in-grub2-how-819474/)

---

### Post by pemmarajut on 2010-08-02
Yes, it is always plugged in. I will try that solution anyway.

---

