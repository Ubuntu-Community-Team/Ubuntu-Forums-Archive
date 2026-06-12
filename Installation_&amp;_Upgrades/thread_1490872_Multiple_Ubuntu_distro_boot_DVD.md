---
title: "Multiple Ubuntu distro boot DVD"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by Gyanos422 on 2010-05-22
I want to make a DVD with Ubuntu, Kubuntu, and Xubuntu so i can choose one to start a live session when booting from the disc. I'd like to introduce linux to friends and having a few variations might make it easier to transition. 

All help is always appreciated!

---

### Post by pytheas22 on 2010-05-24
I could see two ways to achieve this.  The first is to [use remastersys]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html") to create a custom build of Ubuntu that has KDE and Xfce (or the kubuntu-desktop and xubuntu-desktop packages if you want the entire application suites that go along with them) installed in addition to Gnome.  Then you could choose which desktop environment to run from the login screen.

A second approach would be to grab ISO images of Ubuntu, Kubuntu and Xubuntu and burn them to your DVD along with a grub2 bootloader that would allow you to boot to each of the ISOs.  You should be able to find instructions for making grub2 boot to an ISO image if you google.

Also keep in mind that most computers can boot to USB these days, so you may want to use that instead of a DVD.  Bootable USB drives have the obvious advantage of being easily modifiable.

---

### Post by C.S.Cameron on 2010-05-24
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

---

### Post by oldfred on 2010-05-24
Same question:

[http://ubuntuforums.org/showthread.php?t=1490141](http://ubuntuforums.org/showthread.php?t=1490141)

CD/DVD multiboot
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/) 		                   		  		  		 		 			 				

If you can boot from a USB C.S.Cameron's link to panticz is a good choice. I have 4 Ubuntu's and several rescue CDs on one 4GB flash drive.

---

