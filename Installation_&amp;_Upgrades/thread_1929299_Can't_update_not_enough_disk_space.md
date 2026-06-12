---
title: "Can't update: not enough disk space"
date: 2012-02-21
forum: Installation &amp; Upgrades
---

### Post by AussieGuy on 2012-02-21
When I try to update, I get an error message telling me that my /boot partition is too full,a nd that I need to free up some disk space.

It is in fact full of old linux kernels; ls /boot:

--
-rw-r--r-- 1 root root  652104 2011-03-02 13:27 abi-2.6.32-30-generic
-rw-r--r-- 1 root root  652104 2011-04-09 09:35 abi-2.6.32-31-generic
-rw-r--r-- 1 root root  652139 2011-04-21 08:52 abi-2.6.32-32-generic
-rw-r--r-- 1 root root  652139 2011-07-30 10:17 abi-2.6.32-33-generic
-rw-r--r-- 1 root root  652395 2011-09-14 10:51 abi-2.6.32-34-generic
-rw-r--r-- 1 root root  115847 2010-04-16 23:01 config-2.6.32-21-generic
-rw-r--r-- 1 root root  116025 2011-03-02 13:27 config-2.6.32-30-generic
-rw-r--r-- 1 root root  116014 2011-04-09 09:35 config-2.6.32-31-generic
-rw-r--r-- 1 root root  116025 2011-04-21 08:52 config-2.6.32-32-generic
-rw-r--r-- 1 root root  116025 2011-07-30 10:17 config-2.6.32-33-generic
-rw-r--r-- 1 root root  116025 2011-09-14 10:51 config-2.6.32-34-generic
drwxr-xr-x 3 root root    6144 2011-11-07 10:36 grub
-rw-r--r-- 1 root root 7968992 2011-03-23 14:01 initrd.img-2.6.32-30-generic
-rw-r--r-- 1 root root 7967545 2011-06-02 10:38 initrd.img-2.6.32-31-generic
-rw-r--r-- 1 root root 7968825 2011-06-30 09:50 initrd.img-2.6.32-32-generic
-rw-r--r-- 1 root root 7999762 2011-11-07 10:39 initrd.img-2.6.32-33-generic
-rw-r--r-- 1 root root 8000191 2011-11-07 10:42 initrd.img-2.6.32-34-generic
drwx------ 2 root root   12288 2010-05-28 13:53 lost+found
-rw-r--r-- 1 root root  160280 2010-03-23 20:37 memtest86+.bin
-rw-r--r-- 1 root root 1691363 2011-03-02 13:27 System.map-2.6.32-30-generic
-rw-r--r-- 1 root root 1691770 2011-04-09 09:35 System.map-2.6.32-31-generic
-rw-r--r-- 1 root root 1690515 2011-04-21 08:52 System.map-2.6.32-32-generic
-rw-r--r-- 1 root root 1690625 2011-07-30 10:17 System.map-2.6.32-33-generic
-rw-r--r-- 1 root root 1691092 2011-09-14 10:51 System.map-2.6.32-34-generic
-rw-r--r-- 1 root root    1196 2010-04-16 23:03 vmcoreinfo-2.6.32-21-generic
-rw-r--r-- 1 root root    1196 2010-06-04 11:58 vmcoreinfo-2.6.32-22-generic
-rw-r--r-- 1 root root    1196 2010-06-11 22:56 vmcoreinfo-2.6.32-23-generic
-rw-r--r-- 1 root root    1196 2010-09-17 04:16 vmcoreinfo-2.6.32-24-generic
-rw-r--r-- 1 root root    1196 2011-03-02 13:29 vmcoreinfo-2.6.32-30-generic
-rw-r--r-- 1 root root    1196 2011-04-09 09:38 vmcoreinfo-2.6.32-31-generic
-rw-r--r-- 1 root root    1196 2011-04-21 08:54 vmcoreinfo-2.6.32-32-generic
-rw-r--r-- 1 root root    1196 2011-07-30 10:19 vmcoreinfo-2.6.32-33-generic
-rw-r--r-- 1 root root    1196 2011-09-14 10:53 vmcoreinfo-2.6.32-34-generic
-rw-r--r-- 1 root root 4043840 2011-03-02 13:27 vmlinuz-2.6.32-30-generic
-rw-r--r-- 1 root root 4043392 2011-04-09 09:35 vmlinuz-2.6.32-31-generic
-rw-r--r-- 1 root root 4035520 2011-04-21 08:52 vmlinuz-2.6.32-32-generic
-rw-r--r-- 1 root root 4036864 2011-07-30 10:17 vmlinuz-2.6.32-33-generic
-rw-r--r-- 1 root root 4040128 2011-09-14 10:51 vmlinuz-2.6.32-34-generic

--

of which I always boot into 2.6.32-34-generic.  So I can probably just delete all the others.  Can I do this without causing a grub or some other error which might cause booting difficulties?  And if so, what is the best way to delete unnecessary kernels in a system-friendly way?

Thanks,
-A.

---

### Post by uRock on 2012-02-21
Open Synaptic and uninstall all of the old kernels. Uninstall all except the _**three**_ for 2.6.32-34. When you do your search, search for 2-6-32 and be sure to select **Status** in the bottom left, then **Installed** in the upper left, so Synaptic will only show the installed kernels.

---

