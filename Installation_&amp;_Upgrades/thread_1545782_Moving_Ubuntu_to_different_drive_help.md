---
title: "Moving Ubuntu to different drive help"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by jznomoney on 2010-08-04
I am going to move my ubuntu to a different drive.  Right now I have it on my primary sata drive in an extended partition.  I want to move the whole installation to a different drive.  Is there any way to do this without reinstalling ubuntu.  Grub is installed onto my 100mb windows 7 boot partition.  Is there a way to make grub point to the moved ubuntu installation on the different drive?  Is there a guide for this kind of setup?

---

### Post by oldfred on 2010-08-04
You can copy it and there are several ways (dd or gparted), but I do not know details as I believe in clean install. A copy will copy UUIDs and grub settings so you still have to manually update fstab and reinstall grub.

If you do a clean install you can copy over your /home and if you have any system wide settings copy those from /etc config files. You can export a list of installed apps and reinstall easily. This is what I do with every new install as a clean install rather than an upgrade. You should also add a partition for a separate /home and copy that data first so then as part of the install you can select that as your location for /home. You have to have set up partitions in advance and use manual install but it is not really difficult.

Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by ezsit on 2010-08-04
I never copy or move partitions, its always easier and quicker to just backup data and reinstall. Why waste the time and effort in moving/copying partitions and dealing with all the little details of UUIDs and GRUB. Yuck!

---

### Post by tommcd on 2010-08-04
I agree. Just do a clean install of Ubuntu 10.04. Just create up a separate /home partition during the install. Make sure your root partition is 10-20GB if you have the space available. You will be up and running again in less than 30 minutes.

---

### Post by libssd on 2010-08-04
> **jznomoney said:**
> I am going to move my ubuntu to a different drive.  Right now I have it on my primary sata drive in an extended partition.  I want to move the whole installation to a different drive.  Is there any way to do this without reinstalling ubuntu.  Grub is installed onto my 100mb windows 7 boot partition.  Is there a way to make grub point to the moved ubuntu installation on the different drive?  Is there a guide for this kind of setup?
Excels at this. You basically make an image backup of your existing installation, then install it in a new location using the standard Ubuntu installer, but preserving all your personal settings, etc. When the installer gets to the partitioning phase, choose manual and define where you want it to be installed, as well as how much space you allocate to swap.

[http://geekconnection.org/remastersys/](http://geekconnection.org/remastersys/)

---

### Post by jznomoney on 2010-08-05
I created a separate home partition.  Thanks for the help guys.

---

