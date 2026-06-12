---
title: "Upgrading kernel causes thumbdrive boot failure"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by derrekito on 2010-07-28
Hi all, 

I downloaded ```
ubuntu-10.04-desktop-i386.iso
``` from the main site and proceeded to use to [Pendrivelinux installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") to install Ubuntu to my 8 Gigabyte USB-memory-stick. (I'm using a 4gig persistence setting.) After running updates (which includes a kernel update) the OS fails to boot.  

I have reinstalled, but am currently holding back major updates until I can gather more information on how to go about upgrading the kernel properly. Please help in this regard. 

I also need to install video drivers.  After activating drivers for my NVIDIA 8600 GTS I receive a pop-up window stating: ```
 SystemError: installArchives() failed 
``` The crash report states ```
 Sorry, the package "initramfs-tools 0.92bubuntu78" failed to install or upgrade.
``` After looking through the error report I found the following under **glxinfo**: ```
 Error: [Errno 2] No such file or directory 
```

Any help is appreciated!

---

### Post by derrekito on 2010-07-29
Bump.

---

### Post by efflandt on 2010-07-29
Certain things on bootable iso on USB are fixed in a squashfs file system, and boot from that before persistent data is mounted.  So if you want to update the kernel or some other things that load initially, you have to do a regular installation on the USB stick/drive, instead of bootable iso.  And in the summary step after you add your user just before installation proceeds, you have to use the Advanced button to put grub in the mbr of the USB stick or drive, instead of default to mbr of your main hard drive.

You can add programs to bootable iso, and certain drivers like for wireless.  But you cannot update the kernel, and I am not sure about proprietary video.  Bootable iso on USB is not very secure anyway, because anyone can boot it without a password.

With 8 GB, you should easily be able to do a regular installation, because I have done that on 4 GB.  But that did not leave much space, so 8 GB is the minimum recommended.

---

### Post by C.S.Cameron on 2010-07-30
efflandt is correct, if you are not satisfied with the kernel that comes with the Live version it is probably best to do a Full install.
However ...
If you absolutely require an upgraded Live USB you can make one using Remastersys:
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

---

### Post by derrekito on 2010-08-03
Thanks for your replies!

---

