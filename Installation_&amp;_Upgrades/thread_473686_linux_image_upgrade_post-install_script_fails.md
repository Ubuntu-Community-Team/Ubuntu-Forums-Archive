---
title: "linux image upgrade post-install script fails"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by xpavement on 2007-06-14
Whenever I attempt to download/install any packages, it looks like apt is attempting to finish some kind of post-install script for: linux-image-2.6.20-16-generic (2.6.20-16.29):

Here is the output:
> 
Setting up linux-image-2.6.20-16-generic (2.6.20-16.29) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
W: mdadm: unchecked configuration file: /etc/mdadm/mdadm.conf
W: mdadm: please read /usr/share/doc/mdadm/README.upgrading-2.5.3.gz .
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.20-16.28 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.20-16.28 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
**expr: non-numeric argument** (is this the problem?)
User postinst hook script [/usr/sbin/update-grub] exited with value 3
dpkg: error processing linux-image-2.6.20-16-generic (--configure):
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 linux-image-2.6.20-16-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any ideas on what to do here?

---

### Post by tyres on 2007-06-14
I've been having a similar problem. What I noticed is that my boot partition seems to be nearly full, so maybe lack of space to re-write the Linux image is the problem. There are a lot of old kernel images in there, which probably aren't necessary to keep (I guess?), so maybe deleting some of them (or moving them elsewhere) would solve the problem. i've not tested that theory out yet.

---

### Post by xpavement on 2007-06-14
Thanks for the idea, but I've been pretty good at removing old kernel images, and my boot file system has 127megs free, so I don't think that is quite it.

---

### Post by xpavement on 2007-06-14
*one* bump

---

### Post by xpavement on 2007-06-15
Running update-grub just plain fails:

> rlingenf@dogget:~$ sudo update-grub
Password:
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
expr: non-numeric argument


A little help?

---

### Post by xpavement on 2007-06-15
Found it myself, noticed expr was used to check the number of the default image in menu.lst, I had this set to 'saved' instead of a number, I changed this to zero and was able to run update-grub. Now I won't get the restart needed notice needed every time I update a package...

---

### Post by gtr225 on 2007-06-16
I use LILO and have the same problem, how do I fix this?

---

### Post by xpavement on 2007-06-16
So every time you update your kernel images, it attempts to run update-grub even though you have lilo setup (which fails)? Maybe there is some configuration inloved to eliminate grub, like you could take running /usr/sbin/update-grub out of the /etc/kernel-img.conf for the postinst/postrm hook fields?

---

### Post by gtr225 on 2007-06-16
I'm sorry let me explain better. What happens is whenever I try to update/install/remove any packages it attempts to run some script for that kernel which dramatically increases the amount of time it takes to perform the requested operation. Eventually I'll get a dialog stating that the kernel script failed. I just wanna know how I can go about fixing that from happening again.

---

### Post by xpavement on 2007-06-16
Yes, so maybe try editing the /etc/kernel-img.conf file so it doesn't attempt to run those scripts anymore?

---

