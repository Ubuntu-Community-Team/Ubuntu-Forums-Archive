---
title: "&quot;Segmentation fault&quot; after &quot;apt-get dist-upgrade&quot; for Hardy"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by littlebat on 2008-11-12
Hi, this is my first post at Ubuntu forum. Thanks for making such a great Distribution.

I am using Xubuntu 8.04. install its "/" and swap on LVM over RAID0. 
After excute "sudo apt-get dist-upgrade" at November 12, 2008 (china local time), when I boot system with newly installed 2.6.24-21-generic kernel, Hardy can't boot. I can boot the old 2.6.24-19-generic kernel. But, after I updated the 2.6.24-19-generic kernel by command "sudo update-initramfs -u -k all", the updated 2.6.24-19-generic kernel cann't boot Hardy yet.

When boot from 2.6.24-21-generic kernel, after "Loading, Please wait..." at the begin of booting, series of "Segmentation fault" appeared.

After several minutes, the "initramfs>" appeared, I execute "cat /proc/modules", nothing appeared. I execute "modprobe", it reported "Segmentation fault", I found there are only three commands under /sbin I executed without this "Segmentation fault", these three commands are "mdadm, mount.ntfs, mount.ntfs-3g". All the other commands under /sbin will get "Segmentation fault" error, they are "depmod lvm modprobe  pkill udevadm dmsetup mdadm mount.fuse rmmod udevd". I knew the reason that system can't boot is it can't execute most of system commands in initramfs. But, I don't know why did this happen and how to fix it.

Before "dist-upgrade", I use 2.6.24-19-generic kernel. 
Below is the information when I execute "sudo apt-get upgrade -s" and "sudo apt-get dist-upgrade -s"

> 
mdx@ubuntu:~/files$ sudo apt-get upgrade -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  bind9-host dnsutils libbind9-30 libisccc30 libisccfg30 linux-generic
  linux-image-generic linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
mdx@ubuntu:~/files$ 

mdx@ubuntu:~/files$ sudo apt-get dist-upgrade -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  libdns35 libisc35 linux-image-2.6.24-21-generic
  linux-restricted-modules-2.6.24-21-generic
  linux-ubuntu-modules-2.6.24-21-generic
The following packages will be upgraded:
  bind9-host dnsutils libbind9-30 libisccc30 libisccfg30 linux-generic
  linux-image-generic linux-restricted-modules-generic
8 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Inst linux-image-2.6.24-21-generic (2.6.24-21.43 Ubuntu:8.04/hardy-updates)
Inst linux-ubuntu-modules-2.6.24-21-generic (2.6.24-21.33 Ubuntu:8.04/hardy-upda
tes)
Inst libisc35 (1:9.4.2.dfsg.P2-2 Ubuntu:8.04/hardy-updates)
Inst libdns35 (1:9.4.2.dfsg.P2-2 Ubuntu:8.04/hardy-updates)
Inst libisccc30 [1:9.4.2-10] (1:9.4.2.dfsg.P2-2 Ubuntu:8.04/hardy-updates)
Inst libisccfg30 [1:9.4.2-10] (1:9.4.2.dfsg.P2-2 Ubuntu:8.04/hardy-updates)
Inst libbind9-30 [1:9.4.2-10] (1:9.4.2.dfsg.P2-2 Ubuntu:8.04/hardy-updates)
Inst bind9-host [1:9.4.2-10] (1:9.4.2.dfsg.P2-2 Ubuntu:8.04/hardy-updates)
Inst dnsutils [1:9.4.2-10] (1:9.4.2.dfsg.P2-2 Ubuntu:8.04/hardy-updates)
Inst linux-generic [2.6.24.19.21] (2.6.24.21.23 Ubuntu:8.04/hardy-updates) []
Inst linux-image-generic [2.6.24.19.21] (2.6.24.21.23 Ubuntu:8.04/hardy-updates)
 []
Inst linux-restricted-modules-2.6.24-21-generic (2.6.24.14-21.51 Ubuntu:8.04/har
dy-updates) []
Inst linux-restricted-modules-generic [2.6.24.19.21] (2.6.24.21.23 Ubuntu:8.04/h
ardy-updates)
Conf linux-image-2.6.24-21-generic (2.6.24-21.43 Ubuntu:8.04/hardy-updates)
Conf linux-ubuntu-modules-2.6.24-21-generic (2.6.24-21.33 Ubuntu:8.04/hardy-upda
tes)
Conf libisc35 (1:9.4.2.dfsg.P2-2 Ubuntu:8.04/hardy-updates)
Conf libdns35 (1:9.4.2.dfsg.P2-2 Ubuntu:8.04/hardy-updates)
Conf libisccc30 (1:9.4.2.dfsg.P2-2 Ubuntu:8.04/hardy-updates)
Conf libisccfg30 (1:9.4.2.dfsg.P2-2 Ubuntu:8.04/hardy-updates)
Conf libbind9-30 (1:9.4.2.dfsg.P2-2 Ubuntu:8.04/hardy-updates)
Conf bind9-host (1:9.4.2.dfsg.P2-2 Ubuntu:8.04/hardy-updates)
Conf dnsutils (1:9.4.2.dfsg.P2-2 Ubuntu:8.04/hardy-updates)
Conf linux-image-generic (2.6.24.21.23 Ubuntu:8.04/hardy-updates)
Conf linux-restricted-modules-2.6.24-21-generic (2.6.24.14-21.51 Ubuntu:8.04/har
dy-updates)
Conf linux-restricted-modules-generic (2.6.24.21.23 Ubuntu:8.04/hardy-updates)
Conf linux-generic (2.6.24.21.23 Ubuntu:8.04/hardy-updates)
mdx@ubuntu:~/files$ 


PS: Here is my installation steps:
1), two harddisk, There are three partitions is raid partition ("fd" flag) in every harddisk , form three raid0 device (/dev/md0, /dev/md1, /dev/md2). Create RAID0 and LVM by [CDlinux]("http://www.cdlinux.info/")0.6.2 livecd;
2), install "/" on /dev/md0, "/home" on LVM over RAID0(include: /dev/md1 and /dev/md2);
3), move "/" from /dev/md0 to LVM;
4), Added /dev/md0 into LVM yet, now, there are three raid0 device under LVM;

Below is my VG config file:
> 
# Generated by LVM2: Wed Nov 12 18:36:11 2008

contents = "Text Format Volume Group"
version = 1

description = "vgcfgbackup -f ./ubuntuvg.vg"

creation_host = "ubuntu"	# Linux ubuntu 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686
creation_time = 1226486171	# Wed Nov 12 18:36:11 2008

ubuntuvg {
	id = "ts36Bu-9vSq-1TG7-AJ3L-Y0nH-gtm2-opnLpN"
	seqno = 23
	status = ["RESIZEABLE", "READ", "WRITE"]
	extent_size = 8192		# 4 Megabytes
	max_lv = 0
	max_pv = 0

	physical_volumes {

		pv0 {
			id = "Aeork6-ojbn-xlel-FJxn-ZEXd-Rm4D-ODSm2f"
			device = "/dev/md1"	# Hint only

			status = ["ALLOCATABLE"]
			dev_size = 4497664	# 2.14465 Gigabytes
			pe_start = 384
			pe_count = 548	# 2.14062 Gigabytes
		}

		pv1 {
			id = "cImSbv-ECVz-Bup3-W9GM-szzb-cDBb-yQjrKY"
			device = "/dev/md2"	# Hint only

			status = ["ALLOCATABLE"]
			dev_size = 4080128	# 1.94556 Gigabytes
			pe_start = 384
			pe_count = 498	# 1.94531 Gigabytes
		}

		pv2 {
			id = "MDdDRo-1Af9-Dmz6-Dzq3-V4Tv-2I0W-68z5rg"
			device = "/dev/md0"	# Hint only

			status = ["ALLOCATABLE"]
			dev_size = 4015744	# 1.91486 Gigabytes
			pe_start = 384
			pe_count = 490	# 1.91406 Gigabytes
		}
	}

	logical_volumes {

		ubuntuswap {
			id = "FNc6qh-3m0R-9IeA-FBFL-jf1H-A1H1-Q0Etsu"
			status = ["READ", "WRITE", "VISIBLE"]
			segment_count = 1

			segment1 {
				start_extent = 0
				extent_count = 192	# 768 Megabytes

				type = "striped"
				stripe_count = 1	# linear

				stripes = [
					"pv0", 0
				]
			}
		}

		ubunturoot {
			id = "Resom2-tiRw-mRrI-OSBl-TWlK-adHC-4CKSZ1"
			status = ["READ", "WRITE", "VISIBLE"]
			segment_count = 3

			segment1 {
				start_extent = 0
				extent_count = 498	# 1.94531 Gigabytes

				type = "striped"
				stripe_count = 1	# linear

				stripes = [
					"pv1", 0
				]
			}
			segment2 {
				start_extent = 498
				extent_count = 356	# 1.39062 Gigabytes

				type = "striped"
				stripe_count = 1	# linear

				stripes = [
					"pv0", 192
				]
			}
			segment3 {
				start_extent = 854
				extent_count = 490	# 1.91406 Gigabytes

				type = "striped"
				stripe_count = 1	# linear

				stripes = [
					"pv2", 0
				]
			}
		}
	}
}


Below is my RAID0 information:
> 
mdx@ubuntu:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid0 sda1[0] sdb5[1]
      2040064 blocks 64k chunks
      
md1 : active raid0 sda6[0] sdb7[1]
      2248832 blocks 64k chunks
      
md0 : active raid0 sda5[0] sdb6[1]
      2007872 blocks 64k chunks
      
unused devices: <none>
mdx@ubuntu:~$ 


My system information: PIII 667MHZ + 256M RAM + (3.2G+4.3G HD) + 17" CRT + Xubuntu 8.04 + (/ on raid0 + lvm + Reiserfs) + Blackbox + Rox-filer &#65288;I haven't installed Xfce4 Desktop&#65289;

I don't know if the prolem is related with my "LVM over RAID0", so I post my system information above.

Have you run into this kind of question? Is it a bug? How to fix it? Thanks very much.

---

### Post by littlebat on 2008-11-13
I have reported it as a bug: [https://bugs.launchpad.net/ubuntu/+bug/297546](https://bugs.launchpad.net/ubuntu/+bug/297546)

---

### Post by littlebat on 2008-12-09
Hi, all. 
I have been stucked at this problem about three weeks. I tried to find the reason of how this occured.

I kept the backup of this system in Vmware, this time, I moved the sytem into ext2 partitions instead of LVM plus RAID0 before. And, I have tried reinstall busybox, initramfs-tools, and build a 2.6.24.7 kernel using config file "/boot/config-2.6.24-22-generic" with common building kernel method in linux(make mrproper; make; make modules_install; mkinitramfs -o /boot/initrd.img-2.6.24.7 2.6.24.7, I modified "MODULES" to "list" in config file "/etc/initramfs-tools/initramfs.conf" because the initrd.img file will bigger than 40M if I keep "MODULES=most" in this situation ). But, all of these effort ended up with the same result as my first post above.

I have reported this as a bug: [https://bugs.launchpad.net/ubuntu/+bug/297546](https://bugs.launchpad.net/ubuntu/+bug/297546) , I noticed, ubuntu removed kernel 2.6.24-21 from the "dist-upgrade" when they recieved this bug, about three days pasted, the kernel 2.6.24-21-generic appeared in "dist-upgrade" again. And, from this on, I can't reproduced this bug. But, Ubuntu has no any response information with this bug to me, so, I don't know if my problem is caused by my mistake or Ubuntu has fixed something but has not feeded back to me. So, I am still stucking in this problem.

I have added some screen snapshots for the boot error messages in VMware. And, an initrd.img-2.6.24-21-generic file has been attached with the bug I reported three weeks ago: [http://launchpadlibrarian.net/19611092/initrd.img-2.6.24-21-generic](http://launchpadlibrarian.net/19611092/initrd.img-2.6.24-21-generic) . If you have any clue, please let me know. 

Thanks very much!

---

