---
title: "Header files do not match uname -r"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by donkeyX on 2008-09-04
Hey guys,

I am trying to install vmware server on hardy herron but have come to a stop when i got the selecting the header files. Basically, my uname will tell me this : 

2.6.24-17-generic

However, when I want to point the inlstallation to my header files there are only these installed : 


don@pluto:~$ ls -la /usr/src
total 3476
drwxrwsr-x  8 root src     4096 2008-09-03 17:51 .
drwxr-xr-x 11 root root    4096 2008-03-20 07:17 ..
lrwxrwxrwx  1 root src       33 2008-09-03 17:51 linux -> ./linux-headers-2.6.24-17-generic
drwxr-xr-x 20 root root    4096 2008-06-05 08:33 linux-headers-2.6.24-18
drwxr-xr-x  6 root root    4096 2008-06-05 08:33 linux-headers-2.6.24-18-generic
drwxr-xr-x 20 root root    4096 2008-09-01 18:12 linux-headers-2.6.24-19
drwxr-xr-x  6 root root    4096 2008-09-01 18:12 linux-headers-2.6.24-19-generic
drwxr-xr-x  7 root root    4096 2008-05-31 20:30 rpm
drwxr-sr-x 10 root src     4096 2008-06-27 17:59 tora-1.3.22
-rw-r--r--  1 root src    19723 2007-12-12 21:03 tora_1.3.22-5.diff.gz
-rw-r--r--  1 root src      776 2007-12-12 21:03 tora_1.3.22-5.dsc
-rw-r--r--  1 root src  3496227 2007-10-29 07:03 tora_1.3.22.orig.tar.gz


Also, when i try to install the versions of the headers for my kernel it fails becuase there are none that match. So, my question is: can i just upgrade the kernel is is there a place that i can download the correct headers. This is just a little strange as this is the only pc that is having this problem as the others have more recent headers and i did not have a problem?

thanks in advance

---

### Post by donkeyX on 2008-09-10
bump.... no help for this???

---

### Post by cariboo on 2008-09-10
Have you tried booting in to the latest kernel? You have the headers for -2.6.24-19-generic listed. You may need to update grub to reflect the latest kernel.

Jim

---

### Post by lazyart on 2008-09-10
Sounds like you've updated the kernel but you are booting into an older one (were you having problems with it an reverted?).  Interrupt the boot process and select a newer kernel.  You should then be able to complete the vmware server install.

---

### Post by Pumalite on 2008-09-10
sudo apt-get install linux-headers-`uname -r`

---

### Post by donkeyX on 2008-09-22
Hey Guys, 

thanks for the help but how do you update the kernal headers and what would i update them to? 2.6.24.19?

and when i run the update headers it looks for the old version and does not find it.. i would prefer to update to the newer version if possible?


donkey@pluto:/usr/share/sqldeveloper$ uname -r
2.6.24-17-generic
[1]+  Done                    ./sqldeveloper.sh
donkey@pluto:/usr/share/sqldeveloper$ sudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-2.6.24-17-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.24-17-generic has no installation candidate
donkey@pluto:/usr/share/sqldeveloper$

---

