---
title: "Loop in boot during use of Ubuntu server 6.06"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by kortved on 2008-04-09
I do not have much Linux experience, but have tried to install a LAMP server from a CD with Ubuntu 6.06 on a rather small old HP vectra X86/5 cpu with 163 MByte and a 2,6 Gbyte Master HD and a 13 Gbyte Slave HD.
Installation takes some time, and I used the partition-tool during install to erase the hd0 and make the three default "partitions" etc. I chose DK-lanuage, keyboard, gave a username etc.
I succeded in install, at the machine ejected the UBUNTU CD and was ready to reboot.
When it boots, GNU GRUB v 097 writes the following:

root (hd0,4)
kernel /vmlinux-2.6-15-51-server root=/dev/mapper/Ubuntu-root ro quit splash
initrd /initrd.img-2.6.15.51-server
savedefault
boot

.... but the GRUB "boot" cmd gets my HW to boot from start, including the HW/BIOS testing, and then repeating the above root etc ....

What have I done wrong ?
Regards from Kim, a male dane

PS: I have posted this on "absoluter beginner talk" but a second thought got me to post it under this forum.

---

### Post by Rocket2DMn on 2008-04-09
Did you change GRUB at all?  I think it should look more like
```
root (hd0,4)
kernel /boot/vmlinux-2.6-15-51-server root=/dev/mapper/Ubuntu-root ro quit splash
initrd /boot/initrd.img-2.6.15.51-server
savedefault
boot
```
Unless it chroots, but I don't really know.  You can try reinstalling GRUB with the Super Grub Disk - [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by adrian15 on 2008-04-10
> **kortved said:**
> 
root (hd0,4)
kernel /vmlinux-2.6-15-51-server root=/dev/mapper/Ubuntu-root ro quit splash
initrd /initrd.img-2.6.15.51-server
savedefault
boot


Please remove quiet and splash words from menu.lst and tell us where it reboots. 
Trying some driver? Setting local hour?

Have you tried booting from Super Grub Disk -> Super Grub Disk (with Help) -> Linux -> Boot Linux
to see if it boots?


adrian15

---

### Post by confused57 on 2008-04-10
Maybe this will help:
[http://ubuntuforums.org/showpost.php?p=3042597&postcount=3](http://ubuntuforums.org/showpost.php?p=3042597&postcount=3)

---

