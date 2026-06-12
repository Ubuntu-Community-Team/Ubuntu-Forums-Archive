---
title: "[SOLVED] No grub folder in /boot"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by svanheulen on 2008-09-22
I was going to add Windows to my grub menu and I don't seem to have a grub folder in /boot. Where do I find menu.lst?
```
person@place:~$ ls -l /boot/
total 18877
-rw-r--r-- 1 root root  422667 2008-08-21 00:46 abi-2.6.24-19-generic
-rw-r--r-- 1 root root   80049 2008-08-21 00:46 config-2.6.24-19-generic
-rw-r--r-- 1 root root 7985925 2008-08-26 10:32 initrd.img-2.6.24-19-generic
-rw-r--r-- 1 root root 7985957 2008-08-21 19:27 initrd.img-2.6.24-19-generic.bak
-rw-r--r-- 1 root root  905170 2008-08-21 00:46 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root 1921464 2008-08-21 00:46 vmlinuz-2.6.24-19-generic
```

---

### Post by svanheulen on 2008-09-22
No one? Grub is there when I boot up so it must be installed someplace, how do I find where?

---

### Post by caljohnsmith on 2008-09-22
How about posting the output of:
```
sudo fdisk -lu
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
grub> quit
```
That should give us a good place to start. :)

---

### Post by svanheulen on 2008-09-22
I figured it out, my boot partition wasn't mounted. I thought it was because when I tried 'sudo mount /boot' it said 'mount: /dev/sda1 already mounted or /boot busy' but then I realized my boot partition isn't sda1 because it's on a nvraid. So once I got it mounted everything was where it should be.

---

