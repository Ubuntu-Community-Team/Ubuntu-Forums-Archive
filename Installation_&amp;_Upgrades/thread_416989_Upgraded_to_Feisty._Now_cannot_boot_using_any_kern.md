---
title: "Upgraded to Feisty. Now cannot boot using any kernel."
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by bankie on 2007-04-21
Yesterday I started the update to Feisty through update manager. During the process there was an error with the nvidia-glx drivers and update manager wanted to revert everything back to the previous versions. While doing this the system hard locked. I can longer boot using any of the normal kernels in GRUB startup. I can boot using the recovery mode option but everything stops with a tty error when trying to access the root partition and it spits me out to the initramfs prompt.

I cannot mount any of my drives from initramfs. There are no sd* devices in /dev so i get a "file not found" error.


I can mount the root partition using the 7.04 LiveCD. Here's what I've done so far:

Ctrl+Alt+F2
sudo mount -t ext3 /dev/sdb1 /media/oldroot
sudo chmod /media/oldroot
sudo dpkg --configure -a

dpkg starts to run but then stops with "Processing was halted because there were too many errors".


Thanks for any insight you all may be able to give.

---

### Post by Matt Yun on 2007-04-21
You should read through this thread:  [WARNING: latest kernel (2.6.20-14.23) broken for many. Download will fail till fixed.]("http://ubuntuforums.org/showthread.php?t=408253")

---

### Post by bankie on 2007-04-21
Thanks for the reply. I read through all 31 pages but fix they describe doesn't work for me. I have 2 initrd files in /boot: initrd.img-2.6.17-10-generic and initrd.img-2.6.17-11-generic. There are no .bak files in the boot directory for me to restore. I did notice that there is a vmlinuz-2.6.20-15-generic in addition to the other 2 kernels but there is no initrd file pertaining to it.

---

### Post by Matt Yun on 2007-04-21
I know that the following advice may draw flames, but it will probably be quicker if you simply install Feisty from scratch.  While you undoubtedly could try to make a new initrd image from chroot in a LiveCD session, that would probably take more time than a new install.

---

