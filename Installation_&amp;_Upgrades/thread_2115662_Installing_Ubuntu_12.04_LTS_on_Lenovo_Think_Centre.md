---
title: "Installing Ubuntu 12.04 LTS on Lenovo Think Centre"
date: 2013-02-13
forum: Installation &amp; Upgrades
---

### Post by AMKawam on 2013-02-13
When I tried installing Ubuntu 12.04 on Lenovo Think Centre I faced some problems with the UEFI boot mode. 

When I installed Ubuntu in dual boot with windows7, the PC booted windows7 directly without displaying the boot window. 

When I installed Ubuntu on the whole drive, the system displayed the following error:
Error 1962: No operating system Found. 

Apparently the problem was with the (U)EFI boot mode. 

Anyhow, I solved these problems, but it took me some time!

Solution:

1) Install Ubuntu 10.04, on the whole drive, or side by side Windows. Ubuntu will run without any problems with the boot, this is because it uses legacy boot mode. 

2) Run the Ubuntu 12.04 installation from a CD/USB stick.

3) In the disk partitioning section, choose "Something Else"

4) Delete the Ubuntu 10.04 partition while keeping the Linux swap partition as is.

5) Choose the now freed disk space for a new partition and set the entry point as "root" (/). 

6) Set the boot loader to install on the whole disk (sda), then proceed with the installation.

When you reboot you will no longer face the no OS error. But you will face another error that says:
"invalid arch independent ELF magic". To fix this, it is simple and all you need to do is:

1) Run Ubuntu 12.04 from the CD/USB. 

2) In the terminal enter the following lines of code:
(In this example sda1 is the Ubunutu 12.04 partition | use sudo if you do not have permission to run any of these commands)

```

mount /dev/sda1 /mnt
mount -t proc proc /mnt/proc
mount -t sysfs sys /mnt/sys
mount -o bind /dev /mnt/dev
chroot /mnt
apt-get update
apt-get install grub
grub-install /dev/sda1
grub
root (hd0,0)
setup (hd0)
quit
update-grub
exit
reboot

```

And that should do it!

Have a nice Ubuntu!!

---

