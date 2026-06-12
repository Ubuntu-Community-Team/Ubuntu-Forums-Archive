---
title: "After upgrading only memtest boot option displayed"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by ozwolverine on 2010-05-02
Hello everybody,

I just upgraded my ubuntu 9.10 to ubuntu 10.04 through system update, during installation I got some errors telling me that partition /boot/ was about to run out of space, so I deleted through console old files in /boot/, I left only those with todays date, I thought those were the ones needed to boot my new ubuntu. but after restaring system the only options I get in boot meny are, memtest and windows 7. What can I do to solve this issue? maybe just copying some files to /boot/ partition? or editing some kind of file?

next there is a ls -lh I run from the CD from my /boot/ partition:
ls /media/fdb07b7f-ec0e-4de0-bda8-8651cbd0d44f/
grub                          initrd.img-2.6.28-15-generic
initrd.img-2.6.24-24-generic  initrd.img-2.6.28-16-generic
initrd.img-2.6.27-14-generic  initrd.img-2.6.31-21-generic
initrd.img-2.6.28-11-generic  initrd.img-2.6.32-21-generic
initrd.img-2.6.28-13-generic  lost+found
initrd.img-2.6.28-14-generic  memtest86+.bin
root@ubuntu:~# ls -lh /media/fdb07b7f-ec0e-4de0-bda8-8651cbd0d44f/
total 62M
drwxr-xr-x 2 root root 1.0K 2010-05-01 14:22 grub
-rw-r--r-- 1 root root 7.1M 2010-05-01 13:40 initrd.img-2.6.24-24-generic
-rw-r--r-- 1 root root 7.3M 2010-05-01 13:39 initrd.img-2.6.27-14-generic
-rw-r--r-- 1 root root 6.5M 2010-05-01 13:17 initrd.img-2.6.28-11-generic
-rw-r--r-- 1 root root 6.5M 2010-05-01 13:17 initrd.img-2.6.28-13-generic
-rw-r--r-- 1 root root 6.5M 2010-05-01 13:17 initrd.img-2.6.28-14-generic
-rw-r--r-- 1 root root 6.5M 2010-05-01 13:17 initrd.img-2.6.28-15-generic
-rw-r--r-- 1 root root 6.5M 2010-05-01 13:17 initrd.img-2.6.28-16-generic
-rw-r--r-- 1 root root 7.0M 2010-05-01 13:40 initrd.img-2.6.31-21-generic
-rw-r--r-- 1 root root 7.6M 2010-05-01 14:10 initrd.img-2.6.32-21-generic
drwx------ 2 root root  12K 2009-06-08 16:34 lost+found
-rw-r--r-- 1 root root 157K 2010-03-23 09:37 memtest86+.bin


ls of grub directory on /boot/ gives this output:

ls -lh /media/fdb07b7f-ec0e-4de0-bda8-8651cbd0d44f/grub/
total 175K
-rw-r--r-- 1 root root  197 2009-06-08 11:48 default
-rw-r--r-- 1 root root   15 2009-06-08 11:48 device.map
-rw-r--r-- 1 root root 7.9K 2009-06-08 11:48 e2fs_stage1_5
-rw-r--r-- 1 root root 7.8K 2009-06-08 11:48 fat_stage1_5
-rw-r--r-- 1 root root 1.0K 2010-05-01 13:58 grubenv
-rw-r--r-- 1 root root   16 2009-06-08 11:48 installed-version
-rw-r--r-- 1 root root 8.5K 2009-06-08 11:48 jfs_stage1_5
-rw-r--r-- 1 root root 4.3K 2010-05-01 14:22 menu.lst
-rw-r--r-- 1 root root 4.3K 2010-05-01 14:22 menu.lst~
-rw-r--r-- 1 root root 7.2K 2009-06-08 11:48 minix_stage1_5
-rw-r--r-- 1 root root 9.5K 2009-06-08 11:48 reiserfs_stage1_5
-rw-r--r-- 1 root root  512 2009-06-08 11:48 stage1
-rw-r--r-- 1 root root 106K 2009-06-08 11:48 stage2
-rw-r--r-- 1 root root 9.1K 2009-06-08 11:48 xfs_stage1_5


cat of file device.map file in grub dir is:
 cat /media/fdb07b7f-ec0e-4de0-bda8-8651cbd0d44f/grub/device.map 
(hd0)	/dev/sda


Options without comments in file menu.lst in grub dir from /boot/ is:
default		0
timeout		10

title		Ubuntu 10.04 LTS, memtest86+
root		(hd0,4)
kernel		/memtest86+.bin
quiet

title		Other operating systems:
root

title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


thanks a lot for any help.





thanks a lot

---

