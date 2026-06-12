---
title: "Inatalling Ubuntu from DVD to an external HD"
date: 2015-05-07
forum: Installation &amp; Upgrades
---

### Post by brian64 on 2015-05-07
Very new to Ubuntu.  I have a Windows 7 laptop that has 3 drives (SSD 128GB, 2 1 TB drives).   I just purchased a 4 TB external drive and want to install Ubuntu on it.  I burned the image and was off.  When I got to the screen about where to put Ubuntu and boot load, I got very confused.  I was hoping I could do this...use a bootable CD then only use the 4 TB drive for everything.  Is that possible?  This is for website/database development/testing.  Should I dual boot?  Just not sure where to go from here.

Thanks,

Brian

---

### Post by yancek on 2015-05-07
Yes you can install it to the 4TB drive.  If you have windows on another drive, it would probably be simpler to put the Ubuntu Grub bootloader in the master boot record of that drive (the 4TB).  That is, if you are using MBR to boot and not UEFI/GPT which is very different.  The naming conventions for Linux for hard drives and partitions are very different and you should have at least a minimal understanding of that.  The link below gives a good tutorial on installing Ubuntu in dual-boot.  Use the manual "Something Else" option when you begin the install so you have some control and can see what is happening.

  [http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

