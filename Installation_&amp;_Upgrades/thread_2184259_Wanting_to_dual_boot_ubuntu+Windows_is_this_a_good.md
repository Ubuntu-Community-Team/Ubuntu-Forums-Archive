---
title: "Wanting to dual boot ubuntu+Windows is this a good guide? (link in post)"
date: 2013-10-28
forum: Installation &amp; Upgrades
---

### Post by bakuzjw on 2013-10-28
New user here. I want to dual boot ubuntu and windows on my computer. I have two HDs one will be for windows the other for ubuntu. I found this guide [http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/). Is it a good guide to  follow? Should I be doing something else? Any help would be welcomed.

---

### Post by LuvLinuxOS on 2013-10-28
> New user here. I want to dual boot ubuntu and windows on my computer. I  have two HDs one will be for windows the other for ubuntu. I found this  guide [http://www.linuxbsdos.com/2012/07/23...2-hard-drives/]("http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/"). Is it a good guide to  follow? Should I be doing something else? Any help would be welcomed.

Why do you want to dual boot? I would Google the topic and review more than one guide. They way Grub and Linux and Windows recognize hdd partitions is different but easily translatable!!!!  That might be the biggest thing to get dual booting working!!!  Know where every OS is in your partition tables on each and every system.  Good Luck!!!

Be Blessed!!!

---

### Post by oldfred on 2013-10-28
Welcome to the forums.

Not many guides for multiple drive installs, so that is one I often link to for details and screen shots. But I do not suggest the separate /boot for most desktops and do suggest smaller / (root) of 10 to 25GB and rest of drive as data or /home.

You do want to be sure to install grub2's boot loader to the same drive as Ubuntu install. My screenshot show the combo box with the default sda (I actually use sdd as default so my test installs can use sda as location for grub boot loader).

Other than using Something Else so you get the option on where to install grub, the install is like many other dual boot installs just that you can partition drive anyway you desire as Windows is not on same drive.

 Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

 Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

