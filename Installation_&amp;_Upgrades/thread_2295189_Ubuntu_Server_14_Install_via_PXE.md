---
title: "Ubuntu Server 14 Install via PXE"
date: 2015-09-16
forum: Installation &amp; Upgrades
---

### Post by nathanhawthorne12 on 2015-09-16
Evening guys.

Currently have

DHCP
TFTP

all setup correctly on my synology NAS

I have a default file of

```
default menu.c32prompt 0
timeout 100
ONTIMEOUT chainlocal


LABEL local
        MENU LABEL Boot local hard drive
        LOCALBOOT 0


LABEL chainlocal
	MENU LABEL Chain boot to local hard drive
	KERNEL chain.c32
	APPEND hd0


LABEL Linux_Mint_17
        MENU LABEL Install Linux Mint 17 x86
        KERNEL images/Linux-Mint-17/vmlinuz
	APPEND root=/dev/nfs boot=casper netboot=nfs nfsroot=192.168.1.1:/volume1/isoNFS/images/Linux-Mint-17 


initrd=images/Linux-Mint-17/initrd.lz nosplash --


LABEL Ubuntu-Server-14.04
        MENU LABEL Install Ubuntu Server 14.04 x64
        KERNEL images/Ubuntu-Server-14/vmlinuz
	APPEroot=/dev/nfs ND boot=casper netboot=nfs nfsroot=192.168.1.1:/volume1/isoNFS/images/Ubuntu-Server-14 


initrd=images/Ubuntu-Server-14/initrd.gz nosplash --


LABEL Ubuntu-Server-14.04-x86
        MENU LABEL Install Ubuntu Server 14.04 x86
        KERNEL images/Ubuntu-Server-14-x86/vmlinuz
	APPEND boot=casper netboot=nfs nfsroot=192.168.1.1:/volume1/isoNFS/images/Ubuntu-Server-14-x86 initrd=images/Ubuntu-


Server-14-x86/initrd.lz nosplash --



```

The test laptop DOES boot via PXE and it gets as far as USBHID: USB HID CORE DRIVER 

the next line is a shell with 

 busybox v1.21.1 built in shell
(Initramfs)

Does anyone have any ideas why this would be?

---

### Post by MAFoElffen on 2015-09-16
Try using acpi=off as a kernel boot option... on the client during it's boot. (refer to post #3 of my sticky in my sig line)

---

