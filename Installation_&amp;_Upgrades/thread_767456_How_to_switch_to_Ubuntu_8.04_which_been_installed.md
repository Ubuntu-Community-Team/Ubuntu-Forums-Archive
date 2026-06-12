---
title: "How to switch to Ubuntu 8.04 which been installed?"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by HolyJoe on 2008-04-25
Hi,

I do an upgrade from ubuntu 7.10 to ubuntu 8.04 via an internet connection. After download all necessary packages, Upgrade-Manager begin install and prompt me: how to config menu.lst, then I choice 'keep the local that current installed'. The installation is ok, but when I restart computer, the old ubuntu 7.10 boot menu appears. 

I'd a question: 
How to let grub to boot the new installed ubuntu 8.04?

1.My old ubuntu 7.10 ls -l /boot/ output:
```
[SIZE="4"]total 35108
-rw-r--r-- 1 root root  424317 2008-02-12 18:39 abi-2.6.22-14-generic
-rw-r--r-- 1 root root  422607 2008-04-11 00:51 abi-2.6.24-16-generic
-rw-r--r-- 1 root root   75311 2008-02-12 18:39 config-2.6.22-14-generic
-rw-r--r-- 1 root root   79964 2008-04-11 00:51 config-2.6.24-16-generic
drwxr-xr-x 2 root root    4096 2008-04-26 06:13 grub
-rw-r--r-- 1 root root 7218522 2008-03-10 22:31 initrd.img-2.6.22-14-generic
-rw-r--r-- 1 root root 7219417 2008-03-10 21:19 initrd.img-2.6.22-14-generic.bak
-rw-r--r-- 1 root root 7447997 2008-04-26 06:18 initrd.img-2.6.24-16-generic
-rw-r--r-- 1 root root 7447900 2008-04-26 06:12 initrd.img-2.6.24-16-generic.bak
-rw-r--r-- 1 root root  103204 2007-09-28 18:06 memtest86+.bin
-rw-r--r-- 1 root root  823535 2008-02-12 18:39 System.map-2.6.22-14-generic
-rw-r--r-- 1 root root  899892 2008-04-11 00:51 System.map-2.6.24-16-generic
-rw-r--r-- 1 root root 1764536 2008-02-12 18:39 vmlinuz-2.6.22-14-generic
-rw-r--r-- 1 root root 1904248 2008-04-11 00:51 vmlinuz-2.6.24-16-generic
[/SIZE]
```

2. My /boot/grub/menu.lst:
```
[SIZE="4"]title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=d22dd597-f5dd-4d34-9929-bc854db202fb ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=d22dd597-f5dd-4d34-9929-bc854db202fb ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet

title           Windows Vista/Longhorn (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1

[/SIZE]
```

---

