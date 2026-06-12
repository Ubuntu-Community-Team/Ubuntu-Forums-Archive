---
title: "Windows 10 (UEFI) installation issue"
date: 2016-06-29
forum: Installation &amp; Upgrades
---

### Post by mike_kzc on 2016-06-29
Hi All,

Just got a new computer (Dell Inspiron15 5000 series). The OS currently is windows10 (UEFI).

When I use the a USB a drive to install the Ubuntu 16.04, I got the following errors:

*****************************************
[6.514576] sd 2:0:0:0: [sdb] No caching mode page found
[6.514622] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[10.856437] blk_update_request: I/O error, dev sdb sector 3862264
[10.858252] blk_update_request: I/O error, dev sdb sector 3862264
[10.858274] blk_update_request: I/O buffer I/O error on dev sdb, logical block 482783, async page

Busybox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu) built-in shell (ash)

Enter "help" for a list of built-in commands.

(initramfs)

*********************************************

Please advise. Thanks you very much.

Mike

---

### Post by oldfred on 2016-06-29
Did you verify that ISO you downloaded was correct?
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Did you boot flash drive in UEFI boot mode?
       
 Ubuntu UEFI install ISO
Also links on how to create a bootable DVD or USB flash drive, from Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Easy way to create UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 
           
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

See install steps you should follow in link in my signature.

These are Dell laptops, my Dell SFF desktop Haswell based system with 16.04 just works, but newer Skylake systems may need even newer kernel & drivers than in distribution.

 Kernel 4.6 has Dell & Alienware improvements including 9350
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers)
Dell XPS 8900 i7-6700 pcie_aspm=off (also: Asus X555UB)
[http://askubuntu.com/questions/760257/ubuntu-16-04-failed-clean-install-on-new-hard-drive](http://askubuntu.com/questions/760257/ubuntu-16-04-failed-clean-install-on-new-hard-drive)
Dell with Ubuntu 14.04 pre-installed & question on special drivers (Sputnik)
[http://askubuntu.com/questions/764857/dell-isos-for-ubuntu-14-04-and-16-04-for-linux-based-dell-laptops](http://askubuntu.com/questions/764857/dell-isos-for-ubuntu-14-04-and-16-04-for-linux-based-dell-laptops)
Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241)

---

