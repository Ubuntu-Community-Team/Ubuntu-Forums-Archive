---
title: "Upgraded from 10.04 to 10.10 and getting error"
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by nmahadkar on 2010-12-25
```
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic
Segmentation fault
E: mkinitramfs failure cpio 139 gzip 0
update-initramfs: failed for /boot/initrd.img-2.6.32-22-generic
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1

```

I have not idea where to start.

---

### Post by Rubi1200 on 2010-12-26
Hi and welcome to the forums :)

Go to Applications > Accessories > Terminal and run the following commands:

```
sudo apt-get install -f

sudo dpkg --configure -a

sudo apt-get update
```

If any of the commands show errors, post them back here please.

Thanks.

---

### Post by frio on 2011-01-23
The error I am getting is similar (ref thread [http://ubuntuforums.org/showthread.php?t=1670292](http://ubuntuforums.org/showthread.php?t=1670292)).

I tried the commands you suggest and the first two yield the same exact error/results. The third completes without issue. I'm running Ubuntu Server v10.04.1 LTS. It's been up and running flawlessly for several months now. Just recently when doing a routine upgrade check I noticed this error using apt-get. I have searched the net and all I can find are some bugs related to installing/running Ubuntu from an USB stick. I am not running on an USB stick.

All the partitions on the machine, mainly the boot partition, has plenty of space. The machine continue to run fine and I am able to install other package updates using apt-get.

Any clues? I have none at this point.

---

