---
title: "PXE Boot Ubuntu"
date: 2012-05-24
forum: Installation &amp; Upgrades
---

### Post by mcihangir on 2012-05-24
Hi UBUNTU community,

I want to make a Node that should boot Ubuntu over network from a Server PC. System overview is shown below;

[[IMG]http://img406.imageshack.us/img406/9997/figure1f.jpg[/IMG]](http://imageshack.us/photo/my-images/406/figure1f.jpg/)


Node : 
* Node is a SBC (Single Board Computer). 
* CPU DM&P Vortex86DX 1.0 GHz
* NIC(Network Interface Cart ) support PXE Boot.
* OS : Should be Ubuntu 9.10 Karmic Koala

Server PC:
* Desktop PC
* CPU Intel Pentium E2180
* OS : Centos 6.2

I have a problem at Node side. I try to explain my problem stage by stage;

Stage 1)

I have prepared Server PC like as  DHCP Sever , TFTP Server. Server PC is running very well.  I have created /tftpboot folder on Server PC. I have put "pxelinux.0, menu.c32, memdisk, mboot.c32, chain.c32, vesamenu.c32" in /tftpboot folder on Server PC. Also I have created "pxelinux.cfg" and "images" folder in /tftpboot folder on Server PC. 


Stage 2)

There is a Compact Flash Socket on Node PC (SBC). First, I have put in a 1GB Compact Flash to Node PC. And I have installed Ubuntu 9.10 through the Compact Flash use a USB CD-ROM at Node PC. And Ubuntu 9.10 is running very well from booting the Compact Flash at Node PC. Stage 2 is shown below;

[[IMG]http://img824.imageshack.us/img824/4185/figure2c.jpg[/IMG]](http://imageshack.us/photo/my-images/824/figure2c.jpg/)


Stage 3) 

I have copied all files from Compact Flash to /tftpboot/images/Ubuntu folder in  Server PC.
Stage 3 is shown below;

[[IMG]http://img337.imageshack.us/img337/2668/figure3.jpg[/IMG]](http://imageshack.us/photo/my-images/337/figure3.jpg/)


Stage 4)

I have edit /tftpboot/pxelinux.cfg/default file for boot linux kernel and initrd. I have run Node PC after finished configuration. Stage 4 is shown below;

[[IMG]http://img18.imageshack.us/img18/9827/figure4t.jpg[/IMG]](http://imageshack.us/photo/my-images/18/figure4t.jpg/)


After these stages, Node PC is loading kernel from the known location;
Loading /images/Ubuntu/boot/vmlinuz..............
Loading /images/Ubuntu/boot/initrd..............
..............
..............

I have received this error message  after at the end of work;

Gave up waitng for root device. Comman problems:
-Boot args (cat /proc/cmdline)
 -....
......
......
ALERT! does not exist. Dropping to a shell!



My aim is to run Node PC with diskless.  I want to use RAM disk root file system.
I want to Linux kernel to decompress and load into a RAM disk to be used as the root file system. 

I guess this problem is about "initial RAM disk" but I don't know that how to I configure Installed Ubunutu 9.10 for "initial Ram disk".  I found very much docs about "Diskless Linux" or "Ram Disk" but I need help-point shot.

How can I do  "RAM disk support" for installed Ubuntu 9.10 in Node PC side?
What should I do after Stage 2 for  support "initial RAM disk" over Installed Ubuntu 9.10 on Compact Flash?

Thanks,
Cihangir

---

