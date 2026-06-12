---
title: "PC Startup"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by Vman446 on 2009-12-31
Well first off i dont know if this is the right place to post this.
But after instalation of ubuntu and when i restart the comp it says i have to choose my operating system or something.

says Ubuntu 9.10 and this in safe mode
and 2 more i dont know and win7 wich was my last op before i installed ubuntu.

whats the problem here? what do i need to do?
And can i go back to win 7 if it wont be fixed?

Thanks.

---

### Post by mr clark25 on 2010-01-01
if you can boot into ubuntu, run this command in the terminal:
sudo update-grub

then reboot and see if your win7 is there.


if you can not boot into ubuntu, i had a similar problem. i fixed it by booting into a live cd, and running these commands:
sudo bash
mkdir -p /mnt/temp/boot
mount /dev/sda5 /mnt/temp/
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
chroot /mnt/temp
grub-install --recheck /dev/sda
update-grub
exit

the third command may need changed.

run this:
sudo fdisk -l

that will help you find what partition your linux installation is on. replace /dev/sda5 with whatever partition your linux is on.


hope that helps.

---

### Post by Vman446 on 2010-01-01
Thanks for the reply, i will try this out!

---

### Post by Vman446 on 2010-01-01
and btw, do u know how i can install the regular msn messenger from microsoft on Ubuntu? because cam chats dont work with aMSN :confused:

It just says its cancelled

---

### Post by mr clark25 on 2010-01-01
try it with wine. 

command:
sudo apt-get install wine

then right-click the windows file and select "run with wine"

wine usually works with windows files. (.exe)

---

### Post by Vman446 on 2010-01-01
where do i put this command? im a complete beginner with Ubuntu. 
Installed it today

Mr_clarck this is what i got putting ur sudo update-gurb command intro therminal;

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-16-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
raymond@raymond-desktop:~$ 
raymond@raymond-desktop:~$ 
```

---

### Post by mr clark25 on 2010-01-01
it is just telling you that it found two linux images, a memtest86, and a windows 7 bootloader. you should now be able to reboot and select windows 7 to start.

try restarting and loading into the grub menu. windows 7 should now be there.

---

