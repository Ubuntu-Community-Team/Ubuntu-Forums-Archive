---
title: "Can I use debootstrap and install ssh before rebooting?"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by sclough on 2006-08-19
Here is my delima.  I am trying to install ubuntu server on a remote server that I only have ssh access to.  The company I lease the server from will only install Debian (or one of the Redhat family) because ubuntu is a "desktop" distro.  Anyway, they don't care what I use, but they will only install Debian.

So, I have Debian 3.1 installed.  I thought about changing my sources and doing an apt-get update, apt-get dist-upgrade, but I tried that on a virtual machine and it did not work completely and I seemed to get a mixed system that was part Sarge and part Dapper.  (If anyone has had this work, I'd love to hear about it).

Anyway, here's what I've been trying to do:  I took an unused partition and used debootstrap to get the barebones installed.  I copied all the necessary files out of etc and set up a proper fstab.  At this point, I could install a dapper kernel, modify grub to boot that kernel, cross my fingers and reboot the box, except for the simple fact that if the box came back up successfully I would have no ssh to being able to remote in with ](*,) 

I have tried apt-get install ssh, but it complains because ubuntu-base is not installed, but I cannot get that to install inside the chroot environment.  So, I guess my question is:

1.  Is there a way to install ubuntu-base inside the chrooted envioronment I created with debootstrap?  (Do I need to try to install and configure the dchroot package to get this to work?)
2.  Is there a way to install ssh so that I can then install the kernel and reboot and still be able to get into the system?
3.  What kernel should I use?  I noticed a "server" kernel.  Do I need that, or just the standard 686 kernel?  (This is not exotic hardware, just an Intel celeron chip with scsi drives.)
4.  Assuming I can get this working, I assume there is an option for grub so that if booting into my new dapper fails, it will fall back and boot into debian (They both have their own root partitions, so they could both conceivably be used).

Thanks for any help, I've read and read on this one and almost gotten there.  I really want ubuntu-server...

---

