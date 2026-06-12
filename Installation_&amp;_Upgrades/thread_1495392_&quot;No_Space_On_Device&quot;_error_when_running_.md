---
title: "&quot;No Space On Device&quot; error when running update-initramfs"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by ravinandan on 2010-05-28
Hello All,
I'm trying to compile and install new kernel      **2.6.32.14 **in my ubuntu karmic.
After compiling source and executing the deb package for the kernel, I tried to run update-initramfs but got "No space on device" error.
My /boot partition size is 100 MB and is currently having 37MB free.
After I run the update-initramfs command I noticed that space in /boot got depleted and soon came to naught which led to no space error thrown by gzip.
I believe the resultant gzipped archive is no more than 20MB...then why is the whole 37MB is being used up? Please correct me If I'm wrong here otherwise I might be left with no choice but to increase the size of /boot partition.

Is there anyway I can make update-initramfs to use the temporary space from other drives(may be /tmp) when creating gzipped archive?


Would appreciate if someone would help me on this.

Thanks,
Ravi

---

### Post by ravinandan on 2010-05-30
Just an update:
Apparently the new initrd.img took 68MB, hence the no space error.
I increased the size /boot partition to accommodate the file.
Quite an jump from 8MB file size of other initrd image files.

# ls -lh
total 111M
-rw-r--r--. 1 root root 615K 2009-10-16 23:33 abi-2.6.31-14-generic
-rw-r--r--. 1 root root 615K 2010-03-12 14:05 abi-2.6.31-20-generic
-rw-r--r--. 1 root root 616K 2010-03-24 17:01 abi-2.6.31-21-generic
-rw-r--r--. 1 root root 619K 2010-03-24 17:19 abi-2.6.31-21-generic-pae
-rw-r--r--. 1 root root 109K 2010-03-24 17:01 config-2.6.31-21-generic
-rw-r--r--. 1 root root 110K 2010-03-24 17:19 config-2.6.31-21-generic-pae
-rw-r--r--. 1 root root 112K 2010-05-27 01:52 config-2.6.32.13
drwxr-xr-x. 2 root root 3.0K 2010-05-30 19:28 grub
-rw-r--r--. 1 root root 7.3M 2010-04-30 23:25 initrd.img-2.6.31-21-generic
-rw-r--r--. 1 root root 8.1M 2010-05-28 23:23 initrd.img-2.6.31-21-generic-pae
[COLOR=Red]-rw-r--r--  1 root root  68M 2010-05-30 19:33 initrd.img-2.6.32.13[/COLOR]
drwx------  2 root root  12K 2010-04-23 22:55 lost+found
-rw-r--r--. 1 root root 126K 2009-10-23 21:41 memtest86+.bin
-rw-r--r--. 1 root root 1.6M 2010-03-24 17:01 System.map-2.6.31-21-generic
-rw-r--r--. 1 root root 1.7M 2010-03-24 17:19 System.map-2.6.31-21-generic-pae
-rw-r--r--. 1 root root 1.7M 2010-05-27 01:52 System.map-2.6.32.13
-rw-r--r--. 1 root root 1.2K 2009-10-16 23:36 vmcoreinfo-2.6.31-14-generic
-rw-r--r--. 1 root root 1.2K 2010-03-12 14:07 vmcoreinfo-2.6.31-20-generic
-rw-r--r--. 1 root root 1.2K 2010-03-24 17:03 vmcoreinfo-2.6.31-21-generic
-rw-r--r--. 1 root root 1.2K 2010-03-24 17:21 vmcoreinfo-2.6.31-21-generic-pae
-rw-r--r--. 1 root root 3.8M 2010-03-24 17:01 vmlinuz-2.6.31-21-generic
-rw-r--r--. 1 root root 3.8M 2010-03-24 17:19 vmlinuz-2.6.31-21-generic-pae
-rw-r--r--. 1 root root 3.9M 2010-05-27 01:52 vmlinuz-2.6.32.13
-rw-r--r--. 1 root root 559K 2010-05-23 11:22 xen-4.0.0.gz
lrwxrwxrwx. 1 root root   12 2010-05-29 11:36 xen-4.0.gz -> xen-4.0.0.gz
lrwxrwxrwx. 1 root root   12 2010-05-29 11:36 xen-4.gz -> xen-4.0.0.gz
lrwxrwxrwx. 1 root root   12 2010-05-29 11:36 xen.gz -> xen-4.0.0.gz
-rw-r--r--. 1 root root 7.8M 2010-05-23 11:22 xen-syms-4.0.0

Thanks,
Ravi

---

