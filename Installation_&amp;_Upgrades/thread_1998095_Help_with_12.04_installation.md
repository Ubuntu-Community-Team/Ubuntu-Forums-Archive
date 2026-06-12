---
title: "Help with 12.04 installation"
date: 2012-06-06
forum: Installation &amp; Upgrades
---

### Post by D0gb0y on 2012-06-06
Hello all,

First off let me just say thanks in advance for any help offered on this.

I am a complete newb to Linux. I have built a new system with a quad core and decent amount of ram. Instead of putting Windows 7 on it I decided to go with Ubuntu 12.04 64bit.

I am not doing anything complicated just 1 x 160gb HDD for the installation drive and a single operating system. The command given to Ubuntu was erase the drive and install fresh. During the installation, towards the end, I had a fatal error message regarding the boot installer. I have tried reinstalling several times and get the same error message each time.

Now when i run the installation CD it tells me that 12.04 is already installed ( but will not boot without the CD ). I guess this must be something to do with the GRUB, but every instruction i try to follow from related posts seems to end in an error message.  

Any help would be greatly welcomed!!!!

Kind regards

---

### Post by dino99 on 2012-06-06
so boot from the livecd to reinstall grub by opening a terminal and run:

sudo grub-install /dev/sda
sudo update-grub

exit and try to boot from hdd

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by D0gb0y on 2012-06-06
Hi Dino99 thanks for your speedy reply!

I saw this advice you posted for someone else and i tried it earlier but got this message


ubuntu@ubuntu:~$ sudo grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$

---

### Post by SVEN1 on 2012-06-06
Nuke and Boot the hard drive and try a fresh install
[http://www.dban.org/]("http://www.dban.org/")

---

