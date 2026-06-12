---
title: "How to install Win7 from Ubuntu? 11.10"
date: 2011-11-03
forum: Installation &amp; Upgrades
---

### Post by Tjal Lee on 2011-11-03
I've got a usb installer and a disc installer but in both cases it only gives me custom installation and upgrade installation but I can't make a new partion to install Win7 on.

I need a few programs from Windows to work with that don't operate on Ubuntu.


Im using ubuntu 11.10 btw.

---

### Post by darkod on 2011-11-03
Option 1: You might consider installing Win7 inside VirtualBox. In this case just download and install VirtualBox, and set up a virtual machine Win7 inside it.

Option 2: When using the Win7 DVD to install, it will now show the ubuntu partition to resize it and make space for windows because it can't see it. And it's not recommended to shrink it with windows anyway. In this case, you should boot into live mode with the ubuntu cd (or usb), open Gparted and resize the partitions you want in order to create unallocated space. Then boot with the win7 dvd and use that unallocated space.

If you need to use win7 only occasionally option 1 is much better. Plus, when shrinking the ubuntu partition it can possibly break ubuntu. So if it serves your purpose, installing win7 inside VB is much better.

---

### Post by Tjal Lee on 2011-11-03
I tried Virtualbox but can't seem to get it to work.

I get this error:

Kernel driver not installed (rc=-1908)

Please install the virtualbox-dkms package and execute 'modprobe vboxdrv' as root.

and


Failed to open a session for the virtual machine Windows 7.

The virtual machine 'Windows 7' has terminated unexpectedly during startup with exit code 1.

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Machine
Interface: IMachine {5eaa9319-62fc-4b0a-843c-0cb1940f8a91}



 
Isn't there a way to install Win7 as dual boot option from Ubuntu 11.10?

---

### Post by darkod on 2011-11-03
To install as dual boot and from within Ubuntu, no. You need to boot with the win7 dvd and previously have unallocated space or better a partition formatted as ntfs. Then tell the win7 installer to install onto this ntfs partition.

I have tried VB few times, and it worked fine straight away. You might want to locate some VB forum and investigate the error messages you are getting. I think it would be worth it as you only need win7 occasianally.

---

### Post by tnt533 on 2011-11-04
Also keep in mind that installing Windows after Ubuntu will rewrite the mbr and windows will revert to using its own boot-loader instead of grub. You will have to boot to a live cd after the installation of Windows and reinstall grub to be able to boot into Ubuntu.

---

### Post by Mark Phelps on 2011-11-04
Notice the part where you have to BOOT from CD in order to make the partition changes. That's because you can't make changes to a partition that is mounted, and it must be mounted in order to use it.

---

