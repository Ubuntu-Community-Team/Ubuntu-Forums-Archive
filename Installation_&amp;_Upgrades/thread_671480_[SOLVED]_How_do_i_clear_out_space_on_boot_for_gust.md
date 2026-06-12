---
title: "[SOLVED] How do i clear out space on /boot for gusty upgrade?"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by wormeyman on 2008-01-18
I apparently don't have enough free space for the upgrade i heard that i can remove the old kernels how would i go about this?

> eric@ubuntu:/boot$ ls -la
total 173558
drwxr-xr-x  4 root root    3072 2008-01-14 23:28 .
drwxr-xr-x 23 root root    4096 2008-01-17 20:40 ..
-rw-r--r--  1 root root  239811 2006-07-18 16:27 abi-2.6.12-10-386
-rw-r--r--  1 root root  239770 2005-10-10 06:16 abi-2.6.12-9-386
-rw-r--r--  1 root root  266735 2006-08-02 22:09 abi-2.6.15-26-386
-rw-r--r--  1 root root  286242 2006-12-05 14:42 abi-2.6.17-10-386
-rw-r--r--  1 root root  285721 2006-12-05 14:47 abi-2.6.17-10-generic
-rw-r--r--  1 root root  286242 2007-03-13 16:46 abi-2.6.17-11-386
-rw-r--r--  1 root root  285721 2007-03-13 16:51 abi-2.6.17-11-generic
-rw-r--r--  1 root root  411006 2007-04-15 01:01 abi-2.6.20-15-386
-rw-r--r--  1 root root  414210 2007-04-15 01:07 abi-2.6.20-15-generic
-rw-r--r--  1 root root  411070 2007-12-17 22:17 abi-2.6.20-16-386
-rw-r--r--  1 root root  414274 2007-12-17 22:24 abi-2.6.20-16-generic
-rw-r--r--  1 root root   64125 2006-07-18 15:06 config-2.6.12-10-386
-rw-r--r--  1 root root   64135 2005-10-10 05:12 config-2.6.12-9-386
-rw-r--r--  1 root root   69903 2006-08-02 19:49 config-2.6.15-26-386
-rw-r--r--  1 root root   75289 2006-12-05 12:38 config-2.6.17-10-386
-rw-r--r--  1 root root   74707 2006-12-05 13:20 config-2.6.17-10-generic
-rw-r--r--  1 root root   75289 2007-03-13 14:42 config-2.6.17-11-386
-rw-r--r--  1 root root   74707 2007-03-13 15:25 config-2.6.17-11-generic
-rw-r--r--  1 root root   83269 2007-04-14 22:04 config-2.6.20-15-386
-rw-r--r--  1 root root   83234 2007-04-14 22:33 config-2.6.20-15-generic
-rw-r--r--  1 root root   83252 2007-12-17 19:07 config-2.6.20-16-386
-rw-r--r--  1 root root   83217 2007-12-17 19:36 config-2.6.20-16-generic
drwxr-xr-x  3 root root    1024 2008-01-14 23:29 grub
-rw-r--r--  1 root root 5288907 2006-08-10 06:33 initrd.img-2.6.12-10-386
-rw-r--r--  1 root root 4937612 2006-08-09 14:45 initrd.img-2.6.12-9-386
-rw-r--r--  1 root root 8774972 2006-10-06 23:31 initrd.img-2.6.15-26-386
-rw-r--r--  1 root root 8205338 2007-05-06 21:43 initrd.img-2.6.17-10-386
-rw-r--r--  1 root root 7115470 2007-02-02 11:14 initrd.img-2.6.17-10-386.bak
-rw-r--r--  1 root root 8283955 2007-05-06 21:42 initrd.img-2.6.17-10-generic
-rw-r--r--  1 root root 7203760 2006-12-14 05:39 initrd.img-2.6.17-10-generic.bak
-rw-r--r--  1 root root 8205757 2007-05-06 21:42 initrd.img-2.6.17-11-386
-rw-r--r--  1 root root 7116267 2007-04-14 10:01 initrd.img-2.6.17-11-386.bak
-rw-r--r--  1 root root 8285350 2007-05-06 21:42 initrd.img-2.6.17-11-generic
-rw-r--r--  1 root root 7169885 2007-05-06 19:44 initrd.img-2.6.17-11-generic.bak
-rw-r--r--  1 root root 8247735 2007-05-06 21:47 initrd.img-2.6.20-15-386
-rw-r--r--  1 root root 8246746 2007-05-06 21:40 initrd.img-2.6.20-15-386.bak
-rw-r--r--  1 root root 8285720 2007-05-06 21:41 initrd.img-2.6.20-15-generic
-rw-r--r--  1 root root 8285715 2007-05-06 21:39 initrd.img-2.6.20-15-generic.bak
-rw-r--r--  1 root root 8250559 2008-01-14 23:27 initrd.img-2.6.20-16-386
-rw-r--r--  1 root root 8250228 2007-09-14 19:15 initrd.img-2.6.20-16-386.bak
-rw-r--r--  1 root root 8287725 2008-01-14 23:28 initrd.img-2.6.20-16-generic
-rw-r--r--  1 root root 8286853 2007-09-14 19:16 initrd.img-2.6.20-16-generic.bak
drwxr-xr-x  2 root root   12288 2006-08-09 14:41 lost+found
-rw-r--r--  1 root root   94600 2006-10-20 04:44 memtest86+.bin
-rw-r--r--  1 root root  897419 2006-07-18 16:28 System.map-2.6.12-10-386
-rw-r--r--  1 root root  897159 2005-10-10 06:16 System.map-2.6.12-9-386
-rw-r--r--  1 root root  726461 2006-08-02 22:09 System.map-2.6.15-26-386
-rw-r--r--  1 root root  713661 2006-12-05 14:42 System.map-2.6.17-10-386
-rw-r--r--  1 root root  728778 2006-12-05 14:47 System.map-2.6.17-10-generic
-rw-r--r--  1 root root  714815 2007-03-13 16:46 System.map-2.6.17-11-386
-rw-r--r--  1 root root  729932 2007-03-13 16:51 System.map-2.6.17-11-generic
-rw-r--r--  1 root root  789067 2007-04-15 01:03 System.map-2.6.20-15-386
-rw-r--r--  1 root root  806942 2007-04-15 01:08 System.map-2.6.20-15-generic
-rw-r--r--  1 root root  789196 2007-12-17 22:18 System.map-2.6.20-16-386
-rw-r--r--  1 root root  807071 2007-12-17 22:25 System.map-2.6.20-16-generic
-rw-r--r--  1 root root 1207230 2006-07-18 16:27 vmlinuz-2.6.12-10-386
-rw-r--r--  1 root root 1206555 2005-10-10 06:16 vmlinuz-2.6.12-9-386
-rw-r--r--  1 root root 1414781 2006-08-02 22:09 vmlinuz-2.6.15-26-386
-rw-r--r--  1 root root 1574463 2006-12-05 14:42 vmlinuz-2.6.17-10-386
-rw-r--r--  1 root root 1636700 2006-12-05 14:47 vmlinuz-2.6.17-10-generic
-rw-r--r--  1 root root 1574521 2007-03-13 16:46 vmlinuz-2.6.17-11-386
-rw-r--r--  1 root root 1635958 2007-03-13 16:51 vmlinuz-2.6.17-11-generic
-rw-r--r--  1 root root 1677036 2007-04-15 01:01 vmlinuz-2.6.20-15-386
-rw-r--r--  1 root root 1745100 2007-04-15 01:07 vmlinuz-2.6.20-15-generic
-rw-r--r--  1 root root 1678348 2007-12-17 22:17 vmlinuz-2.6.20-16-386
-rw-r--r--  1 root root 1747372 2007-12-17 22:24 vmlinuz-2.6.20-16-generic


---

### Post by zvacet on 2008-01-18
In synaptic find **linux-image** and delete all exept one with higher number.You cam free moe space with 

```
sudo apt-get autoremove
```

```
sudo apt-get clean
```

---

### Post by wormeyman on 2008-01-18
Thanks looks like it worked.

> eric@ubuntu:~$ cd /boot &&ls -la
total 104843
drwxr-xr-x  4 root root    3072 2008-01-18 13:32 .
drwxr-xr-x 23 root root    4096 2008-01-17 20:40 ..
-rw-r--r--  1 root root  411006 2007-04-15 01:01 abi-2.6.20-15-386
-rw-r--r--  1 root root  414210 2007-04-15 01:07 abi-2.6.20-15-generic
-rw-r--r--  1 root root  411070 2007-12-17 22:17 abi-2.6.20-16-386
-rw-r--r--  1 root root  414274 2007-12-17 22:24 abi-2.6.20-16-generic
-rw-r--r--  1 root root   83269 2007-04-14 22:04 config-2.6.20-15-386
-rw-r--r--  1 root root   83234 2007-04-14 22:33 config-2.6.20-15-generic
-rw-r--r--  1 root root   83252 2007-12-17 19:07 config-2.6.20-16-386
-rw-r--r--  1 root root   83217 2007-12-17 19:36 config-2.6.20-16-generic
drwxr-xr-x  3 root root    1024 2008-01-18 13:32 grub
-rw-r--r--  1 root root 7115470 2007-02-02 11:14 initrd.img-2.6.17-10-386.bak
-rw-r--r--  1 root root 7203760 2006-12-14 05:39 initrd.img-2.6.17-10-generic.bak
-rw-r--r--  1 root root 7116267 2007-04-14 10:01 initrd.img-2.6.17-11-386.bak
-rw-r--r--  1 root root 7169885 2007-05-06 19:44 initrd.img-2.6.17-11-generic.bak
-rw-r--r--  1 root root 8247735 2007-05-06 21:47 initrd.img-2.6.20-15-386
-rw-r--r--  1 root root 8246746 2007-05-06 21:40 initrd.img-2.6.20-15-386.bak
-rw-r--r--  1 root root 8285720 2007-05-06 21:41 initrd.img-2.6.20-15-generic
-rw-r--r--  1 root root 8285715 2007-05-06 21:39 initrd.img-2.6.20-15-generic.bak
-rw-r--r--  1 root root 8250559 2008-01-14 23:27 initrd.img-2.6.20-16-386
-rw-r--r--  1 root root 8250228 2007-09-14 19:15 initrd.img-2.6.20-16-386.bak
-rw-r--r--  1 root root 8287725 2008-01-14 23:28 initrd.img-2.6.20-16-generic
-rw-r--r--  1 root root 8286853 2007-09-14 19:16 initrd.img-2.6.20-16-generic.bak
drwxr-xr-x  2 root root   12288 2006-08-09 14:41 lost+found
-rw-r--r--  1 root root   94600 2006-10-20 04:44 memtest86+.bin
-rw-r--r--  1 root root  789067 2007-04-15 01:03 System.map-2.6.20-15-386
-rw-r--r--  1 root root  806942 2007-04-15 01:08 System.map-2.6.20-15-generic
-rw-r--r--  1 root root  789196 2007-12-17 22:18 System.map-2.6.20-16-386
-rw-r--r--  1 root root  807071 2007-12-17 22:25 System.map-2.6.20-16-generic
-rw-r--r--  1 root root 1677036 2007-04-15 01:01 vmlinuz-2.6.20-15-386
-rw-r--r--  1 root root 1745100 2007-04-15 01:07 vmlinuz-2.6.20-15-generic
-rw-r--r--  1 root root 1678348 2007-12-17 22:17 vmlinuz-2.6.20-16-386
-rw-r--r--  1 root root 1747372 2007-12-17 22:24 vmlinuz-2.6.20-16-generic
eric@ubuntu:/boot$ 


---

