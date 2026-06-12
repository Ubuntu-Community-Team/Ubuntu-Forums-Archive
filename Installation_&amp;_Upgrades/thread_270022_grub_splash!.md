---
title: "grub splash!"
date: 2006-10-02
forum: Installation &amp; Upgrades
---

### Post by hudelfa on 2006-10-02
How can I attach an image to my grub loader.There are two OS in my laptop.The output (kernel lists)  of my /grub/menu.lst is below.

title       Windows XP Media Center Edition
root        (hd0,1)
savedefault
makeactive
chainloader    +1

title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/sda6 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/sda6 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

title           Ubuntu, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
boot

I attached an image but when I rebooted my laptop it gave an error.(could not locate image on (hd0,5)-> sth like this).

This line in the menu lst. is below.

## Splash images!
splashimage (hd0,5)/grub/soft-tux.xpm.gz

#splashimage=(hd0,1)/boot/grub/blu.xpm.gz

How can I decide which partiton is correct above hd0,5 or hd0,1?
Which one is true above?

And the output of my grub directory is below.

root@sony-vaio:/boot/grub# ls -l
total 324
-rw-r--r-- 1 root root  52973 2006-09-30 22:59 36907-Blu.xpm.gz
-rw-r--r-- 1 root root    197 2006-07-26 17:58 default
-rw-r--r-- 1 root root     15 2006-07-26 17:58 device.map
-rw-r--r-- 1 root root   7508 2006-07-26 17:58 e2fs_stage1_5
-rw-r--r-- 1 root root   7332 2006-07-26 17:58 fat_stage1_5
-rw-r--r-- 1 root root   8128 2006-07-26 17:58 jfs_stage1_5
-rw-r--r-- 1 root root   4191 2006-10-02 23:07 menu.lst
-rw-r--r-- 1 root root   4738 2006-09-29 00:12 menu.lst~
-rw-r--r-- 1 root root   4152 2006-09-30 22:43 menu.lst_old
-rw-r--r-- 1 root root   6804 2006-07-26 17:58 minix_stage1_5
-rw-r--r-- 1 root root   9076 2006-07-26 17:58 reiserfs_stage1_5
-rw-r--r-- 1 root root  63092 2006-08-18 23:10 soft-tux.xpm.gz
-rw-r--r-- 1 root root    512 2006-07-26 17:58 stage1
-rw-r--r-- 1 root root 105428 2006-07-26 17:58 stage2
-rw-r--r-- 1 root root   8764 2006-07-26 17:58 xfs_stage1_5


THANKS IN ADVANCE :))

---

### Post by mitch.c on 2006-10-02
Assuming your /boot parition is disk 1, partition 5, then your splashimage statement should be:
```
splashimage=(hd0,5)/grub/soft-tux.xpm.gz
```
The only thing I noticed in your post is your missing the '=' sign. Here's a link to a HOWTO I found useful: [http://ruslug.rutgers.edu/~mcgrof/grub-images/](http://ruslug.rutgers.edu/~mcgrof/grub-images/)

---

### Post by hudelfa on 2006-10-03
I tried but it gave the same message again.Where is the problem?I can not understand.And it makes me angry.](*,)

---

### Post by mitch.c on 2006-10-03
> **hudelfa said:**
> I tried but it gave the same message again.Where is the problem?I can not understand.And it makes me angry.](*,)
Did you try to test your splashimage using the steps here?: [http://ruslug.rutgers.edu/~mcgrof/grub-images/#1.4](http://ruslug.rutgers.edu/~mcgrof/grub-images/#1.4)

I followed this and although I couldn't show my splashimage as described, using TAB for path completion at least helped my know I was using the correct path.

---

