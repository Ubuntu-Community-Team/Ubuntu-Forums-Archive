---
title: "/boot not enough space, what to take out?"
date: 2015-11-19
forum: Installation &amp; Upgrades
---

### Post by anotherusername2 on 2015-11-19
I've been unable to update Ubuntu Trusty for a while because a dialog box keeps popping up that says I don't have enough space on my /boot folder. I'm a beginner-level user, more or less, and don't want to tinker around places I'm not familiar with, so I don't know what to delete. I've looked around the internet and seen some people with this problem but, again, I don't know how different their particular situation is from mine and don't think I can really apply any tips given to them.

Using some terminal instructions I've recently picked up, I got this:

me:~$ df -h /boot
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       236M  157M   67M  71% /boot
me:~$ ls -lhA /boot
total 149M
-rw-r--r-- 1 root root 1.2M Jan 16  2015 abi-3.16.0-30-generic
-rw-r--r-- 1 root root 1.2M Sep  9 19:36 abi-3.16.0-49-generic
-rw-r--r-- 1 root root 1.2M Oct  3 08:19 abi-3.16.0-50-generic
-rw-r--r-- 1 root root 1.2M Oct  8 00:58 abi-3.16.0-51-generic
-rw-r--r-- 1 root root 172K Jan 16  2015 config-3.16.0-30-generic
-rw-r--r-- 1 root root 173K Sep  9 19:36 config-3.16.0-49-generic
-rw-r--r-- 1 root root 173K Oct  3 08:19 config-3.16.0-50-generic
-rw-r--r-- 1 root root 173K Oct  8 00:58 config-3.16.0-51-generic
drwxr-xr-x 5 root root 1.0K Oct 24 09:12 grub
-rw-r--r-- 1 root root  28M Sep 28 09:47 initrd.img-3.16.0-30-generic
-rw-r--r-- 1 root root  28M Sep 28 17:10 initrd.img-3.16.0-49-generic
-rw-r--r-- 1 root root  28M Oct 17 07:39 initrd.img-3.16.0-50-generic
-rw-r--r-- 1 root root  28M Oct 24 09:12 initrd.img-3.16.0-51-generic
drwx------ 2 root root  12K Sep 28 02:00 lost+found
-rw-r--r-- 1 root root 173K Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root 174K Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root 175K Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root 2.7M Jan 16  2015 System.map-3.16.0-30-generic
-rw------- 1 root root 2.7M Sep  9 19:36 System.map-3.16.0-49-generic
-rw------- 1 root root 2.7M Oct  3 08:19 System.map-3.16.0-50-generic
-rw------- 1 root root 2.7M Oct  8 00:58 System.map-3.16.0-51-generic
-rw-r--r-- 1 root root 5.8M Feb 19  2015 vmlinuz-3.16.0-30-generic
-rw------- 1 root root 5.8M Sep  9 19:36 vmlinuz-3.16.0-49-generic
-rw------- 1 root root 5.8M Oct  3 08:19 vmlinuz-3.16.0-50-generic
-rw------- 1 root root 5.8M Oct  8 00:58 vmlinuz-3.16.0-51-generic

---

### Post by ian-weisser on 2015-11-19
Uninstall your two oldest kernels...unless you happen to be running one of them.

The easy way to try first:
```
sudo apt-get autoremove
```

If that doesn't work, then determine which kernel you are running:
```
uname -r
```

Try using apt-get to remove the oldest kernel (unless that's the kernel you are running):
```
sudo apt-get remove linux-image-3.16.0-30-generic
```

---

### Post by anotherusername2 on 2015-11-20
Thanks, sudo apt-get autoremove worked for me!

---

### Post by mörgæs on 2015-11-20
Good, please mark the thread solved.

---

