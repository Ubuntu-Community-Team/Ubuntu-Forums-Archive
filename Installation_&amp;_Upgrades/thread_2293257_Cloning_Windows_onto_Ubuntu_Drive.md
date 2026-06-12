---
title: "Cloning Windows onto Ubuntu Drive"
date: 2015-09-03
forum: Installation &amp; Upgrades
---

### Post by chemist931 on 2015-09-03
Right now I am running Ubuntu off of a USB drive connected to my laptop.  My laptop internal HDD (500GB) has Windows 10 installed on it.  I have order a 1TB SSHD for use in my laptop, as well as an external drive sled.  I plan on installing a clean version of Ubuntu of the SSHD, with a partition limited to 500GB (give or take a few MB).  After I do this, I want to keep my Windows installation, but move it onto the SSHD using the remaining 500GB.  After I complete this, I need to have Ubuntu and Windows on the same drive.  My problem is that I can't find a way to reinstall Windowsdri onto the SSHD without it automatically destroying Ubuntu.  How do I do this without that happening?  I am thinking of installing Ubuntu into the SSHD, creating a disk image of Windows, and applying the image to the SSHD, all with the pre-installed Ubuntu "Disks" application.  Will this work?
Thanks

---

### Post by yancek on 2015-09-03
Install windows first.  If you are going to use MBR rather than UEFI to boot it should not matter.  With windows 10 you should be able to select the partition to install to although I don't know how you would identify it.  If you use MBR, windows will overwrite it if you install Ubuntu first but you can easily use the Ubuntu install medium to re-install Grub.  If you use Uefit, it's a little more complicated.

---

### Post by chemist931 on 2015-09-03
Thanks!  Will do when hard drive gets here.

---

