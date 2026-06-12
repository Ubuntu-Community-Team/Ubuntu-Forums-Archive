---
title: "Ubuntu corrupted after FC9 installation"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by andreselsuave on 2008-05-27
Hello!
I have 1 160GB hard drive with dual boot Ubuntu Hardy / Fedora Core 9:
First I install ubuntu on the whole HD and then resized the partition to fit FC9 on the remaining space. The problem is that now I can't mount ubuntu. I have tried mounting ubuntu in /mnt/sda1 and adding the lines from /boot/grub/menu.lst to Fedora's /boot/grub/menu.lst 
Now I can select Ubuntu in the grub menu, however, it hangs up in the middle of the boot-up. (even in Ubuntu recovery mode). I paste my actual FC9 menu.lst:
```
default=0
timeout=5
splashimage=(hd0,2)/grub/splash.xpm.gz
hiddenmenu
title 		Fedora (2.6.25.3-18.fc9.i686)
root 		(hd0,2)
kernel 		/vmlinuz-2.6.25.3-18.fc9.i686 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
initrd 		/initrd-2.6.25.3-18.fc9.i686.img


title 		Fedora (2.6.25-14.fc9.i686)
root 		(hd0,2)
kernel 		/vmlinuz-2.6.25-14.fc9.i686 ro root=UUID=607f1fe2-24cb-4ccd-85ed-1c6d181c9b43 rhgb quiet
initrd 		/initrd-2.6.25-14.fc9.i686.img


title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9246b051-24c5-428b-87bd-93178ae6926e ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9246b051-24c5-428b-87bd-93178ae6926e ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```

---

### Post by Kevbert on 2008-05-27
Two things you can check. Compare fstab and your menu.lst UUIDs with the command
```
ls /dev/disk/by-uuid -lah 
```
Every time I've installed a linux distro, based on anything other than a Ubuntu derivative, they've been screwed up.
The other is the partition name.  Use
```
sudo fdisk -l
```
Hope this helps

---

### Post by andreselsuave on 2008-05-27
Checked both. Everything's fine ... :/
Thanks 4 ur help though

---

