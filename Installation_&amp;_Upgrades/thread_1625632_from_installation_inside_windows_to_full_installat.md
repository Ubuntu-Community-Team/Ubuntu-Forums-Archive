---
title: "from installation inside windows to full installation"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by jack_the_lad on 2010-11-19
Hello,

I've installed Ubuntu 10.10 on my hard drive inside windows 7. I've set the ubuntu partition size to 10 GB and Ubuntu is my default boot option.

Since I am not using windows any more,and my ubuntu partition size is getting full I was wondering if there is a way to re-install Ubuntu but now over the entire disk with all my configurations and drivers I need. When I installed Ubuntu inside Windows I needed to install additional drivers for my wireless and graphics card. Also, I have changed some configurations and installed many applications. 

Is it possible to reinstall Ubuntu over the entire disk with keeping of additional drivers and settings? 

Cheers

---

### Post by dino99 on 2010-11-19
use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb (4 Gb if suspend/hibernation is used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by jack_the_lad on 2010-11-19
i can't create new partition because ntfs partiton of win7 is over my entire disk, but thanks for your answer

---

### Post by sikander3786 on 2010-11-19
> **jack_the_lad said:**
> i can't create new partition because ntfs partiton of win7 is over my entire disk, but thanks for your answer
You need to shrink that partition to free up some space. Use the partitioning tool that comes with Windows 7 and run chkdsk 3 times before installing Ubuntu.

Also, defrag your drive before resizing.

---

### Post by sikander3786 on 2010-11-19
Sorry I think I mis-understood your post so am making a new post.

If you want to move your Wubi install to a dedicated partition or even the entire disk, you can follow these links.

[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

---

### Post by jack_the_lad on 2010-11-19
> **sikander3786 said:**
> Sorry I think I mis-understood your post so am making a new post.

If you want to move your Wubi install to a dedicated partition or even the entire disk, you can follow these links.

[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

thanks, I think you gave me some ideas. I will run ubuntu installer and then select the option of installation side by side with other operating systems. That should shrink the ntfs and make ext4 for ubuntu. Then I will move all my important files (<10 GB) to my new ext4 which will be on dev/sda3 i think. then I will format dev/sda2 (ntfs) and join it to ext4.

is that possible? :D

---

### Post by sikander3786 on 2010-11-19
But it is recommended that you use the Windows partitioning tool to resize C: drive. I know you don't need anymore after moving Wubi to its own partition but what if the process corrupts Windows and then you'll not be able to access Wubi install as well.

Everything else seems pretty possible.

---

