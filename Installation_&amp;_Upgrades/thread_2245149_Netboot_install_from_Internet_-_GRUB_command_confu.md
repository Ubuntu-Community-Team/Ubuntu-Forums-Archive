---
title: "Netboot install from Internet - GRUB command confusion"
date: 2014-09-21
forum: Installation &amp; Upgrades
---

### Post by lannyma on 2014-09-21
I am trying to follow the steps on this URL:
[https://help.ubuntu.com/community/Installation/NetbootInstallFromInternet](https://help.ubuntu.com/community/Installation/NetbootInstallFromInternet)


HW is an old IBM Desktop that does not have a DVD burner and it cannot boot from a USB. All of the previous Linux installations I've done have used CD or DVD media. The PC has 1 GB of RAM.


Currently, Linux Mint 15 (Mate) 32 bit is installed. Apparently that is EOL. I would like to install Ubuntu 14.04 LTS (Trusty Tahr) but have never tried to do a network install before.


From this page:
[http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/installer-i386/current/images/netboot/)
I downloaded the following files to my Linux Mint Desktop:
boot.img.gz     mini.iso     netboot.tar.gz  pxelinux.0  pxelinux.cfg  and from ubuntu-installer I got initrd.gz and linux which seem to be the 2 files that are used to start the network installation.


I copied the initrd.gz and linux files into /boot as the Wiki page shown above suggests is OK and their owner is root.


On the Linux Mint installation, it shows in Control Center >  Hardware > Disks that the hard drive is /dev/sda and it looks like /boot is /dev/sda1   It shows a 255 MB bootable partition mounted at /boot  


I am trying to install the 32 bit version of Ubuntu 14.04 LTS on this Intel PC.


When am in GRUB and try to follow the steps shown on the Wiki page, I get into trouble. I have tried different commands, but apparently not the correct commands, or the correct sequence of commands. When I use the "boot" command I get "error: you need to load the kernelfirst" message. I thought I had done that with this command at the grub prompt: "linux=/boot/linux" (without the quote marks) but apparently that isn't the correct command.


I have tried at the grub prompt:


root=(hd0,0)
linux=/boot/linux
initrd=/boot/initrd.gz
boot


root=(/dev/sda1)
linux=/boot/linux
initrd=/boot/initrd.gz
boot


and other combinations of grub commands.


GNU Grub version 2.00_13ubuntu3


Questions:
(1) Is it OK that I placed the initrd.gz and linux files into /boot  ? (If not, where should I put them?)
(2) Do I need any additional files into /boot ?
(3) What is the proper sequence of grub commands I need to use to begin the installation?


Thank you, in advance, for your time and your help, which I greatly appreciate! Lanny

---

### Post by lannyma on 2014-09-24
I gave up on the Netboot install. I downloaded the 32 bit Desktop .iso file and burned the DVD on another PC.  Note: After the download finished I verified that the md5sum was correct before burning the DVD.  After burning the DVD it was verified. Early in the installation, at the partitioning step it was very buggy and repeatedly crashed. After 10 or 15 attempts I got past that and completed the installation OK.

---

### Post by oldfred on 2014-09-24
Instructions to use (hd0,0) would only be correct if grub legacy. Since most systems now grub2 hd0,1 would be correct. I edited instructions in link to show default as grub2, but as instructions say you should review other boot stanza to see what is default.

---

