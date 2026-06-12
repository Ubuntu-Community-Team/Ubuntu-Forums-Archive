---
title: "USB Boot problem"
date: 2011-08-05
forum: Installation &amp; Upgrades
---

### Post by earlingy on 2011-08-05
Hi,
I am trying to install Ubuntu 11.04 on my Dell XPS M1530. I am doing so on a clean reformatted hard drive. I downloaded the newest version and created a bootable flash drive using LiLi usb creator.  When I boot from the flash drive,  it starts fine, I see a Ubuntu screen, then I see a bunch of lines of code, and it stops with this message: 

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Invalid argument
Can not mount /devloop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

It does this even if I don't have the hard drive in the computer. I have tried it a couple times and  tried reformatting the hard drive.
Thanks! 
Alex

---

### Post by zealibib slaughter on 2011-08-05
you may have a bad download there, you may want to verify the download: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
you also may have a corrupt install on your flash drive, Ive never used the program that you did to make a bootable flash drive but you may want to try to create the disk again, or maybe use another program like unetbootin.

---

### Post by Hakunka-Matata on 2011-08-05
I agree with Zealibib, unetbootin has been very reliable.  See my signature

---

### Post by earlingy on 2011-08-05
Thanks! That worked.  I am installed and online!  Never trust your roommate to make your Ubuntu USB flash drive...

---

### Post by Hakunka-Matata on 2011-08-05
Ok

---

