---
title: "Installing Ubuntu FROM a USB pendrive"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by Nicarlo on 2008-04-11
Good morning all,

I have just downloaded the lastest ubuntu distro and would like to install it from my pendirve (not to, but from)

I extracted the .iso that i downloaded to the pendrive and then booted up the system starting on the usb hard drive.

Now after doing this i get a "disk Error"

I am pretty sure that this is possible to do but a quick search on google and the forums i have not yet seen anyone ask any questions about it.

could anyone point me into the right direction ?

Thank you very much for your time and help.

---

### Post by Nicarlo on 2008-04-11
after checking the manual i have found this

4.3.3. Adding an ISO image
The installer will look for an Ubuntu ISO image on the stick as its source for additional data needed for the installation. So your next step is to copy an Ubuntu ISO image onto your stick (be sure to select one that fits). The file name of the image must end in .iso. 

If you want to install over the network, without using an ISO image, you will of course skip the previous step. Moreover you will have to use the initial ramdisk from the netboot directory instead of the one from hd-media, because hd-media/initrd.gz does not have network support. 

When you are done, unmount the USB memory stick (umount /mnt) and activate its write protection switch. 

4.3.4. Booting the USB stick
Warning
If your system refuses to boot from the memory stick, the stick may contain an invalid master boot record (MBR). To fix this, use the install-mbr command from the package mbr: 

# install-mbr /dev/sda


but this still seems to not be working. Ill provide you all with some more errors shortly.

---

### Post by Pumalite on 2008-04-11
This might help:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

From another thread:


I have successfully installed both gutsy and feisty on a laptop without cdrom drive using a flash drive and here is the summary:

1. Make flash drive bootable with syslinux
2. Download the vmlinuz and intrid.gz from the ubuntu archives (not the cd ones - this is why people can't mount the flash drive as CD)
3. get the isolinux.cfg from the cd and rename it syslinux.cfg
4. get a copy of an iso you want to install. dont extract or rename the iso.
5. drag those files into a flash drive
6. boot from it and the install shall go normally without needing to mount anything

any details can be found from the internet or this forum. search install edgy from iso (its the same guide done with edgy)

---

