---
title: "Does installation script perform repartitioning like Mint?"
date: 2014-05-30
forum: Installation &amp; Upgrades
---

### Post by A_Linux_User on 2014-05-30
I have used Mint before and liked the installation script.  Is the Ubuntu installation similar?  I want to keep some old partitions.

---

### Post by mastablasta on 2014-05-30
quite similar if not the same.

you can try it in virtual box (you need 2 GB ram and abotu 8 GB disk space to do it).

if oyu keep the old then i suppose you have separate home? if so all you need to do is install the OS to root and then point the home to your /home partition.

---

### Post by A_Linux_User on 2014-05-30
> **mastablasta said:**
> quite similar if not the same.

you can try it in virtual box (you need 2 GB ram and abotu 8 GB disk space to do it).

if oyu keep the old then i suppose you have separate home? if so all you need to do is install the OS to root and then point the home to your /home partition.

The Mint installer writes a new boot secter script that lets you choose which OS you want to run, including M$ WIndows which I have on a different HD.  Does the Ubuntu installer do that?  The Ubuntu Manual seems to say that I would have to rewrite that script myself.

---

### Post by oldfred on 2014-05-31
Yes the os-prober finds your Windows. It has found Windows since the beginning, but there were issues with grub legacy not finding the then new Windows 7.

But if you have two drives, you really want to keep systems separate. And auto install will not necessarily do that.
Much better to use Something Else. If existing partitions you can click change or if creating you can use +. I do prefer to create partitions in advance with gparted.
But vital for two or more drive installs is the combo box at the bottom of the partitioning screen. You can grub installed to the same drive as Ubuntu and keep the Windows boot loader on the Windows drive. Then each drive can work without the other. Some suggest unplugging the Windows drive to avoid any issue what so ever.

 Install to external drive. Also any second drive.
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

### Post by A_Linux_User on 2014-06-01
Thanks for the detailed info.

---

### Post by mastablasta on 2014-06-02
otherwise Ubuntu just adds all available OS (even windows) into Grub menu. you can then move them up or down the menu (e.g. select windows as default) using grub customizer tool or manually by editing config file.

---

