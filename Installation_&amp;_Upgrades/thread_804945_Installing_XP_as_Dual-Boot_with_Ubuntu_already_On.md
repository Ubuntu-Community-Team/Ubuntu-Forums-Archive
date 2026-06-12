---
title: "Installing XP as Dual-Boot with Ubuntu already On"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by cmlewin on 2008-05-23
I already have Hardy Heron on this comp but need a small 20 gig XP partition so I can do work related stuff. I've looked online and most places say that you need XP on first, then to repartition that before you install Ubuntu. Is there a way to install Windows XP on my machine with Ubuntu already on it?

Thanks.

---

### Post by pytheas22 on 2008-05-23
For various reasons it's easier to install Ubuntu after XP has been installed, but it is nonetheless possible to install Windows after Ubuntu with a little extra work.  You'll need first to create a space on the disk for XP using a Linux CD (the XP installer is far too incompetent to be able to shrink a Linux partition), and after XP is installed, you'll need to install grub again.  [SuperGrubDisk]("http://www.supergrubdisk.org/") should allow you to install grub.  I'm not sure if it has a partition editor as well, but if it doesn't, you could always just boot to your Ubuntu live CD, install gparted (sudo apt-get install gparted) and use that.

Also, it's worth mentioning that if you're only going to be using XP for work stuff, it might be more convenient to install Windows inside a virtual machine on Ubuntu.  XP runs very fast for me inside Virtual Box.  The big downside is that you can't really use video acceleration to play games on a virtualized Windows install, but if you're just doing work stuff that probably won't matter.  The big plus is that you can run Windows applications flawlessly without having to reboot.

Finally, don't forget: editing partitions is inherently risky, so make sure to backup important data on the disk before trying this.

---

### Post by anystupidname on 2008-05-23
Good advice by pytheas. I'll second the virtual machine idea but if you decide to still go the dual boot route, I just wanted to mention two useful tools. To repartition you can use the gparted live distro via unetbootin and then to restore grub you can use another unetbootin package with supergrub.

[http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=240127&release_id=580789](http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=240127&release_id=580789) (you'll use the deb here)
[http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=261880&release_id=574776](http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=261880&release_id=574776) (you'll need the exe here)

---

### Post by cmlewin on 2008-05-23
Yeah I installed WINE and that just kept crashing for me. I'm down for virtualbox (which I just installed through apt-get [[though it install virtualbox-ose]] ) but I have no idea how to use it or install windows apps. Is there a simple way to dooooo this?

---

### Post by pytheas22 on 2008-05-23
First you need to install Windows inside Virtual Box--create a new virtual machine and follow the steps, then put your Windows CD in the drive (or point Virtual Box to the ISO on your hard disk) and boot the virtual machine to install Windows.  Once Windows is installed to the virtual hard disk, you can install applications inside it just as you would on a real Windows system.

Keep in mind that there can be some tricky issues related permissions with Virtual Box (at least, there were for me).  If you can't start it, post the problems here and the solutions should be simple.

---

### Post by cmlewin on 2008-05-23
> **pytheas22 said:**
> First you need to install Windows inside Virtual Box--create a new virtual machine and follow the steps, then put your Windows CD in the drive (or point Virtual Box to the ISO on your hard disk) and boot the virtual machine to install Windows.  Once Windows is installed to the virtual hard disk, you can install applications inside it just as you would on a real Windows system.

Keep in mind that there can be some tricky issues related permissions with Virtual Box (at least, there were for me).  If you can't start it, post the problems here and the solutions should be simple.

Sounds good, will do.

You truly are dipped in ubuntu.

---

