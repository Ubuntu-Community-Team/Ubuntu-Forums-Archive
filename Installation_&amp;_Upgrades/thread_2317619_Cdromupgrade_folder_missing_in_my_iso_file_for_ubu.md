---
title: "Cdromupgrade folder missing in my iso file for ubuntu upgradtion"
date: 2016-03-18
forum: Installation &amp; Upgrades
---

### Post by Manoj_Arun_Kumar on 2016-03-18
Hi,

 I am trying to upgrade my ubuntu version from 15.04 to 15.10 through download ISO files.
 When I tried to follow these steps, I am unable to find cdromupgrade folder in my iso files .

Step : Created dir & mounting loop device using following cmd 

	mkdir -p /media/cdrom
	mount -o loop /media/deva/sda2/Ubuntu/ubuntu/ubuntu-15.10-desktop-i386.iso /media/cdrom/


	root@deva-Lenovo-E4325:/media/cdrom# ll -lrth
	total 45K
	lr-xr-xr-x 1 root root    1 Oct 21 21:48 ubuntu -> ./
	-r--r--r-- 1 root root  224 Oct 21 21:48 README.diskdefines
	dr-xr-xr-x 1 root root 2.0K Oct 21 21:48 preseed/
	dr-xr-xr-x 1 root root 2.0K Oct 21 21:48 pool/
	dr-xr-xr-x 1 root root 2.0K Oct 21 21:48 pics/
	dr-xr-xr-x 1 root root 2.0K Oct 21 21:48 dists/
	dr-xr-xr-x 1 root root 2.0K Oct 21 21:48 .disk/
	dr-xr-xr-x 1 root root  18K Oct 21 21:48 isolinux/
	dr-xr-xr-x 1 root root 2.0K Oct 21 21:48 install/
	dr-xr-xr-x 1 root root 2.0K Oct 21 21:48 casper/
	dr-xr-xr-x 1 root root 2.0K Oct 21 21:48 boot/
	dr-xr-xr-x 1 root root 2.0K Oct 21 21:48 ./
	-r--r--r-- 1 root root 3.6K Oct 21 21:48 md5sum.txt
	drwxr-xr-x 5 root root 4.0K Mar 13 19:02 ../
	root@deva-Lenovo-E4325:/media/cdrom# 

Can anyone guide me to upgrade my ubuntu system using downloaded ISO file ?

 Note : I dont have internet connection for using updatemanager -d cmd.


 Thanks
 MAK

---

