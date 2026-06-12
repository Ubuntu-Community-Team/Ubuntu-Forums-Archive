---
title: "need help installing ubuntu"
date: 2015-05-05
forum: Installation &amp; Upgrades
---

### Post by kaitlin3 on 2015-05-05
ok so im installing ubuntu onto my laptop for the first time and since i have always been a windows user im wondering if theres a guide i can read that will teach me how to install ubuntu and how to format my hard drive and the like

---

### Post by dino99 on 2015-05-05
here is a wiki  [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
to avoid mistakes, i propose you choose the custom installation way, instead of the default installer procedure.
First prepare your disk and existing (windows) installation: you may need to clean/shrinck/chkdsk and remove/save some files.
Then , as i remember, windows want to be installed on the first partition. And 4 primary partitions is the maximum allowed; so better to only set 3 primary and 1 extended where  you can set other partitions inside.

That is the first step, then create the partitions for installing ubuntu: / (root) with the 'boot' flag, about 12/15 gb, ext4 format; swap, about 4 gb max; and /home (without limitation), ext4, for your data & settings. This can be done with gparted used from an usb/cdrom.
Then the ubuntu installation can be done. When the installer ask you where you want to install it, select the 'something else' choice to re-use the previous partitions you made with gparted.
 [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[http://gparted.org/](http://gparted.org/)

---

### Post by kaitlin3 on 2015-05-05
thanks for the reply but what i want to do is wipe windows from my hard drive and install ubuntu as the sole os but since im new to ubuntu i have no idea how to format my drive then install ubuntu on it

---

### Post by Bucky Ball on 2015-05-05
Firstly, welcome. 

Download the ISO from [here]("http://www.ubuntu.com/download/desktop"). Go for 14.04.2. Burn the image to a disk or USB. Boot from that and 'Try Ubuntu' when you get to the options. Once at a desktop, launch the Gparted application. Right click the Win partitions (NTFS) and delete them. You want the whole disk as free space, no partitions. 

Back to the desktop. You will find an icon 'Install Ubuntu'. Click it. You can install to the whole disk automatically (you might not like the default set up you get but it can be changed later) or you can choose 'Something Else' and create your partitions manually. Up to you, but the latter will take a bit more research. 

They are the basics. Let us know of any questions you have. A quick search will come up with a heap of pages regarding how to install Ubuntu on your machine. [Here's]("http://www.ubuntu.com/download/desktop/install-ubuntu-desktop") a very basic one for the automatic install. [Here's one]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352") which shows you how to do a 'Something Else' install, with pics. 

Good luck. ;)

---

