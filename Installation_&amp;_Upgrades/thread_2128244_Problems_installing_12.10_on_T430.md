---
title: "Problems installing 12.10 on T430"
date: 2013-03-22
forum: Installation &amp; Upgrades
---

### Post by feitingen on 2013-03-22
I don't even know where to start....
I have a T430 with a 500G HD, a 32G SSD and a 1TB HD.
I've been trying to install using a usb stick created with the ubuntu iso and unetbootin.
It keeps going to kernel panic because it can't find any disks unless i boots it in UEFI mode. That took a few hours to figure out.
Next, i set up my partitions with LVM, formatted my partitions with an external journal on a SSD and started the install which then was hanging for hours until i found this bug from 2011:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/875343](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/875343)

Yes, it is still a problem.
Now, my setup was:
usr, root, home, var on a vg, and the journals for the filesystems and the boot partition on another vg.
So, I merged the vgs, and started again, except i let the installer format the filesystems for me, and the installer completed.
On reboot, grub (which was freshly installed) tried to boot using the /boot from the vg which was merged into the first one.
I spent a couple hours trying to update the mbr, but grub always went back to the old vg name which didn't exist anymore.
So i cleaned all the disks by dding zero to 50MB to the beginning of every partition and every disk and started again.

I created a fresh VG, populated it with lvs for home, usr, root, boot and var. Now it just don't want to boot.
I gave up and created a boot partition on the 32G SSD and now it boots after installing (and cleaning disks and making fresh VG)

Now i have a working install, or so I thought.
I have a Nvidia Quadro NVS 5400M which I wanted to use with CUDA and all that fun stuff, so I installed nvidia-current with apt-get to get the kernel modules and rebooted.
Now i have a 640x480 display because the kernel module wasn't built because the linux headers was missing. Shouldn't that have been a dependency of nvidia-current since it has the DKMS kernel module?
Installed them, and since i got tired of rebooting, i installed kexec-tools so i could kexec into the new kernel with the nvidia module.
apt-get install linux-headers-generic kexec-tools.
It hangs on configuration. I also see that a process associated with debconf frontend is hanging and i assume it's trying to ask me something.
I kill it, do dpkg-reconfigure debconf and set it to dialog so i can answer the questions.
Install again, and i get presented with questions which i answer and configuration succeeds until it hits postconf and then it hangs again.
So I remove kexec-tools and decide to reboot using sudo reboot.
Now my filesystems are not mounting, and I wrote this while doing filesystem checks which check out fine. I didn't even enable the external journal yet.

This really sucks, and there is i don't know how many bug reports in here which i'm not going to bother filling out yet because it's obvious nobody cares when bugs stick around for years.

As an afterthought, you might want to do something to this page as the hardware on it is inaccurate (i sent feedback on it)
[http://www.ubuntu.com/certification/hardware/201112-10223/](http://www.ubuntu.com/certification/hardware/201112-10223/)

I had no idea it would be this much trouble to install ubuntu.

---

