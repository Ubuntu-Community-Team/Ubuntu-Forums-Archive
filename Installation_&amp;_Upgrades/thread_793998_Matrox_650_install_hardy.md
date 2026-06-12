---
title: "Matrox 650 install hardy"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by chubby on 2008-05-14
Hi all.

I have spent many hours trying to install a Matrox p Series 650 video card in Hardy Heron. I have found lots of good information on the forum but nothing seems to work.

I have tried several different versions of the driver made for Linux but I get similar results.
I looked in xorg and it says vesa so the driver is definately not installed.

On install I get this result....
dave@placebo:~$ sudo sh ./matroxdriver_mtx-x86_32-1.4.5.2-installer.run 
Please, enter the directory to extract the files [/home/dave/] 

Creating directory /home/dave/matroxdriver_mtx-x86_32-1.4.5.2
Verifying archive integrity... All good.
Uncompressing Unofficial Matrox Parhelia Driver by tuxx-home.at.......................................................................................................................................................................................






========================================
   Matrox Linux Driver Install Script   
========================================

Installation package v1.4.5.2

Refreshing ld database
Installed mtx_drv.so is the same file as the installer
version, not installing.

Installed v4l_drv.so is the same file as the installer
version, not installing.

Messages are being logged in file /tmp/make.log,
this might take some time.

Compiling mtx.ko ...
ERROR: There has been an error compiling the kernel module. 
       A log file has been created in the file /tmp/make.log

The program returned an error code (1)

Any help would be super.

---

### Post by inzy on 2008-05-23
have you tried the newer version of the driver? there is a 1.4.6.1 out now, that installed fine on ubuntu for me. there were problems later, but it installed ok....

also, what are the contents of /tmp/make.log ?

---

