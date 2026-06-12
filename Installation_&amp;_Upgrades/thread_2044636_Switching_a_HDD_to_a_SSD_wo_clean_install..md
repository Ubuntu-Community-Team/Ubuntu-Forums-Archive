---
title: "Switching a HDD to a SSD w/o clean install."
date: 2012-08-19
forum: Installation &amp; Upgrades
---

### Post by krelverehan on 2012-08-19
Hey guys. I'm looking to switch my old HDD (which is on the fritz) to a new SSD. Just wondering what are my options for moving my currently installed OS to a new SSD without the need for a new install.

I suppose I could do a fresh install, but I _really_ don't want to. Also, my /home/ folder is on a separate partition, that might make things slightly easier.

Is it as simple as plugging in my SSD and transferring everything over to it and messing with GRUB a bit?

Is there a way to turn my currently installed OS into an image file, and reinstall it onto my SSD? I've also read about using programs like clonezilla. Does anybody have any experience on the subject they are willing to share?

Thanks!

---

### Post by Hedgehog1 on 2012-08-19
Hi!

I have done this a few times (moving to all SSDs for the boot drives).

If the SSD is the same size or larger then your hard drive, using the 'ddrescue' tool (dd = Disk to Disk copy; the ddrescue version deals with getting data copied from failing disks).

If the drive is larger than the ssd, I normally shrink the last partition down using gparted so it will fit on the ssd, then use dd or ddrescue to copy.

If your current HDD is acting up, and you need to shrink the data, I would use ddrescue to copy the data to a working hdd that is the same size or larger, shrink the partition on the good hdd, then copy the data to ssd.

I have a usb stick with ubuntu installed and ddrescue that I use to boot systems and do 'dd' or 'ddrescue' when PCs need help like this.

***The Hedge***

:KS

---

### Post by krelverehan on 2012-08-19
Thanks a lot! Just what I was looking for. My SSD is only 60GB compared to the 150GB HDD I'm currently using.

---

### Post by oldfred on 2012-08-19
I am a believer in clean installs. It does a house clean and makes the install work out of the box. 

But you do have to reinstall software. Separate /home does make it easier. Many suggest the new gpt partitioning for SSDs, but then you cannot copy nor clone system.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)

---

### Post by krelverehan on 2012-08-19
Excellent must have reading. Thank you!

---

