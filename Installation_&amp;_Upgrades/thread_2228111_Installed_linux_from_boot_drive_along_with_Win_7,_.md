---
title: "Installed linux from boot drive along with Win 7, can no longer see second drive"
date: 2014-06-05
forum: Installation &amp; Upgrades
---

### Post by kreye009 on 2014-06-05
I tried installing Ubuntu 14.04 (using the 'alongside windows 7' option) for dual boot from a boot drive (not from within windows), but when booting up (choosing between windows and ubuntu) and choosing ubuntu, I got an error saying the root folder could not be found and I then uninstalled ubuntu from Windows . I have 3 drives (2 HD, 1 SSD[Windows 7 boot]) and now can only see two drives, checking windows Disk Management application says the drive is blank but there is no drive letter associated with it, and no apparent way to access it and it appears to be blank (I've attached a picture).

Hopefully my data isn't gone, but it looks like it might be....

Any help appreciated.

---

### Post by oldfred on 2014-06-05
Partitions with Linux formats or if not formatted at all will essentially be the same from Windows or not seen.

From your Ubuntu live installer post this:

sudo parted -l

       Install to external drive. Also any second drive.
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

---

