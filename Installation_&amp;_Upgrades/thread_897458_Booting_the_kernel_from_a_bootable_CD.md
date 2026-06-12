---
title: "Booting the kernel from a bootable CD"
date: 2008-08-22
forum: Installation &amp; Upgrades
---

### Post by stevsurf on 2008-08-22
I have installed Ubuntu 8.04.1 on an external USB hard disk partitioned as follows:
/dev/sdb1 ext3
/dev/sdb2 swap
/dev/sdb3 fat32

My BIOS cannot boot from a USB HDD so I am following the instructions on this web page 

[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

I have got as far as 
> Now that we have corrected the initrd's setup we must use this setup to rebuild the initrd using our new guidelines. To do this you must enter your system by running:

sudo mount --bind /dev /wherever_you_have_mounted_your_system/dev
sudo chroot /wherever_you_have_mounted_your_system
mount -a

I used > sudo mount --bind /dev /dev
sudo chroot /
mount -a

This seemed to worked OK, but when I tried the dpkg-reconfigure command, I received the 

following error message:
> ubuntu@ubuntu:~$ sudo mount --bind /dev /dev
ubuntu@ubuntu:~$ sudo chroot /
root@ubuntu:/# mount -a
root@ubuntu:/# dpkg-reconfigure linux-image-2.6.24-19-generic
Running depmod.
update-initramfs is disabled since running on a live CD
Failed to symbolic-link /boot/initrd.img-2.6.24-19-generic to initrd.img.
root@ubuntu:/# 



Please can someone suggest where I have gone wrong?
Thank you.

---

### Post by ggaaron on 2008-08-22
You should do it like this.
sudo mkdir /mnt/stick
sudo mount /dev/sdb2 /mnt/stick #change sdb2 to meet your needs
sudo mount --bind /dev /mnt/stick/dev
sudo chroot /mnt/stick
mount -a 

Report if it doesn't work. You can read
[http://www.gentoo.org/doc/en/handbook/handbook-amd64.xml?part=1&chap=6](http://www.gentoo.org/doc/en/handbook/handbook-amd64.xml?part=1&chap=6)
parts Mounting the /proc and /dev Filesystems and Entering the new Environment as this is probably what you want to do.

---

