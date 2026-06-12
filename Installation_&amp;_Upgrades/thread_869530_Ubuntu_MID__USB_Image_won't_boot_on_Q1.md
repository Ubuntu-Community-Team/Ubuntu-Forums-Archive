---
title: "Ubuntu MID:  USB Image won't boot on Q1"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by ceoxtc on 2008-07-24
I've spent the last two weeks trying to install Ubuntu MID on my Samsung Q1.  I'm not sure what I'm doing wrong so I'll list my steps here and maybe someone can point me in the right direction:

1) I download the McCaslin install image from [here]("http://cdimage.ubuntu.com/mobile/releases/hardy/")
2) I transfer the image to my blank USB thumb drive (2Gb Sandisk) by using the dd command:  dd if=<image name> of=/dev/sdb

When I do this and view the thumb drive in file manager, the following files are listed:

ldlinux.sys
rootfs.img
install.sh
bootfs.img
vmlinuz
boot.msg
initrd0.img

3) I plug the thumb drive in the Q1 (after having set the Q1 to boot first from 'removable media' and
4) The Q1 boots from the hard drive, which up until 2 days ago had Vista on it.

Thinking somehow that I need to make the USB drive bootable, I downloaded syslinux and installed the bootloader, which added syslinux.cfg to the file list on the USB drive.

5) When I insert the stick in again and boot, no luck - in either the Q1 or my WinXP PC.

So I hooked up an external DVD burner via USB and installed Ubuntu 8.04 from the liveCD.  Now I have Ubuntu on the Q1 with a non-functioning touchpad.

Can anyone tell me why the USB stick won't boot from the USB drive?  Is the McCaslin image supposed to be bootable or should I instead by trying to run the install script from a terminal within Ubuntu?

---

### Post by ceoxtc on 2008-07-26
I was able to do the install.  I hooked up an external burner to the Q1 and using a USB hub, plugged in my keyboard and a USB stick with a copy of the Mccaslin "ultra full" image.  (The image is in the tar zip of the [McCaslin tar file]("http://cdimage.ubuntu.com/mobile/releases/hardy/").

So I fired up Knoppix on the Q1, opened a terminal window and then copied the image to the hard drive (dd if=/dev/sda of=/dev/hda).  Once it was done copying, I unmounted the thumb drive, shutdown Knoppix, unplugged the CD burner and rebooted.

That allowed me to start the MID install directly on the hard drive.  The only hiccup was when it was looking for a missing file on the /dev/sdx drives.  I plugged the thumbdrive back in and it did the install.

MID is now operational on the Q1.  Hope this info helps someone else who may be having problems with the image.:)

---

### Post by JoanneM on 2009-03-25
I've been trying for days to get Ubuntu MID on my Q1. Booting off the USB flash drive didn't work. I installed the desktop version of Ubuntu and copied over the image file to the hard drive as described in the follow-up to this post. When I rebooted - nothing. It just loaded up with the desktop version. I am completely stuck. 

To date I have tried:
 Creating a bootable flash drive 
 Converting the IMG file to ICO on a CD to boot off of
 Copying the IMG file to the hard drive

Nothing has worked with getting Ubuntu MID installed on my Q1. I am desperate and open for suggestions. Anyone?

---

