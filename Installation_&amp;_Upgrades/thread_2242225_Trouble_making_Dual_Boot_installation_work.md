---
title: "Trouble making Dual Boot installation work"
date: 2014-08-31
forum: Installation &amp; Upgrades
---

### Post by Patrick_Mulder on 2014-08-31
Hi,

I bought a new Lenovo E145 ( [http://www.notebookcheck.net/Review-Lenovo-ThinkPad-Edge-E145-Notebook.103235.0.html](http://www.notebookcheck.net/Review-Lenovo-ThinkPad-Edge-E145-Notebook.103235.0.html) ) with Windows 7 pre-installed. There is no DVD drive, so, I need to use USB sticks.

I downloaded the Windows 7 ISO image, and an image of Ubuntu 14.10 to separate USB sticks.

When I install Windows first, Windows boots, but Ubuntu is not loading. When I install Ubuntu, I can see Grub working, but can't boot Windows anymore.

The result:

 /dev/sda1  --> boot partition

/dev/sda4 --> Windows /NTFS

/dev/sda6 --> Linux / ext4

I can mount these under Linux run grub-install, and I can always get a booting Ubuntu.

But I am confused how to get back a booting Windows. I tried to follow: [http://pw999.wordpress.com/2013/12/21/windows-7-linux-dualboot-using-bcd-instead-of-grub/](http://pw999.wordpress.com/2013/12/21/windows-7-linux-dualboot-using-bcd-instead-of-grub/) but without success so far.

Anyone can help? Is there an easier way to get a dual boot setup?
Actually, I might want to have a FreeBSD partition later too.

Thanks a ton!

---

### Post by sbnwl on 2014-08-31
Start your computer, and go into the BIOS setup.
Check if there is any UEFI option enabled.
If yes, the try to change it to LEGACY mode, save and quit BIOS. (If your motherboard allows you to change. Not all motherboard have this option available.)

If you successfully turned the LEGACY mode on, installing Ubuntu in legacy mode will take care of both.

Search on Google about UEFI and Dual boot ...

---

