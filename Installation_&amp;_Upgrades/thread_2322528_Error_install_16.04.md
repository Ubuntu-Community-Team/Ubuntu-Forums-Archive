---
title: "Error install 16.04"
date: 2016-04-28
forum: Installation &amp; Upgrades
---

### Post by LaughingHorse on 2016-04-28
I am installing 16.04 over 15.04 and for the installation rather than let the installation disc "Install 16.04 over 15.04" I chose "Something Else"

Below are screen shots of the disc partitions and the error I am getting.

My root is /dev/sda8/
My home directory is: /dev/sda10

I'm trying to install it on sda8 or is this wrong?[ATTACH=CONFIG]268695[/ATTACH]

I think it is probably something really stupid on my part... like usual :)

[ATTACH=CONFIG]268694[/ATTACH][ATTACH=CONFIG]268693[/ATTACH][ATTACH=CONFIG]268692[/ATTACH]

Thank you in advance for your insight and help!

---

### Post by RobGoss on 2016-04-28
Hello and welcome, This post should help you with this error message you're seeing
[http://askubuntu.com/questions/80455/no-root-file-system-defined-error-while-installing-ubuntu](http://askubuntu.com/questions/80455/no-root-file-system-defined-error-while-installing-ubuntu)

---

### Post by LaughingHorse on 2016-04-29
Thank you Rob. This brings a question.
/dev/sda8/ is already assigned as ext4
It is designated as my root.
/dev/sda10/ is where I have my data.

So do I need to edit sda8 at install again as ext4 ?

---

### Post by RobGoss on 2016-04-29
If you're trying to install Ubuntu only then you can choose to Remove 15.04 and install 16.04 it will do everything for you as far as the partition is concerned

Or you should be able to erase the entire disk and install Ubuntu 1604.

It starts getting complicated when you have multi partitions and want to ether remove one or install another distribution

---

### Post by yancek on 2016-04-29
The error you posted in your initial post means you did not select a partition for the "/" (root filesystem).  If sda8 is the partition with your system files then you click in the main window to highlight it, then click the Change tab below the window and select "/" as the mount point and select ext4 as the filesystem and select the format check box.  This will overwrite the old filesystem files with the new ones.  Also, select sda10 to highlight it and then give it the mountpoint of /home after clicking the change tab and make sure you DO NOT SELECT THE FORMAT box or everything there will also be overwritten.

---

### Post by RobGoss on 2016-04-29
The link I posted in my first reply shows you in detail

---

### Post by oldfred on 2016-04-29
You also show a tiny key icon next to swap. 
If still giving errors, you may want to umount that (swapoff). The installer mounts swap to speed things up, but if mount errors then that can be an issue.

Make sure you do boot installer in UEFI mode, since you have UEFI system. Installer can boot booted in either UEFI or BIOS mode.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by LaughingHorse on 2016-04-29
Thank You all.
Got it installed and updated without a hitch.

Your answers are greatly appreciated!

---

