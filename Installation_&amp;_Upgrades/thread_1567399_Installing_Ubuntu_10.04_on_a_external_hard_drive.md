---
title: "Installing Ubuntu 10.04 on a external hard drive"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by osubunt on 2010-09-03
Hi I have a 320gb hard drive on which I want to install ubuntu while still using it for backup of my main hard drive.  I have two partitions on it - 250gb for backup and 70gb for ubuntu.  Can I just intall the os directly on the hard drive or is there any special stuff I have to do?
Thanks

---

### Post by sgosnell on 2010-09-03
Nothing special, just install it.  You should be able to tell which partition to use from the size.

Well, you do need to have it connected before booting the installer, but nothing other than that.

---

### Post by osubunt on 2010-09-03
Awesome, thanks

---

### Post by oldfred on 2010-09-03
What is the partition formated as. It needs to be a linux format. And you should have a swap partition of 2GB or your RAM memory size if you want to hibernate.

The most important thing is to make sure grub is installed to the external. Use the advanced button (shown in .png below) to choose the external drive, otherwise grub likes to install to sda.

Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24/022f.png](http://members.iinet.net.au/~herman546/p24/022f.png)
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by osubunt on 2010-09-04
Ok, so do I have to format the partition on the drive, or is there any way I can just leave it and let the installer format it?

---

### Post by oldfred on 2010-09-04
You can use manual install and choose the partitions. It will want / (root) and swap. It will also ask for format on / use ext3 or ext4. Swap does not get formated per se.

---

