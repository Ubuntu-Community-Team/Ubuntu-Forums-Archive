---
title: "Dual booting Ubuntu and Elementary OS"
date: 2015-01-29
forum: Installation &amp; Upgrades
---

### Post by alexeix on 2015-01-29
Hi,

I have Ubuntu 14.10 running on my laptop and would like to install Elementary OS, so I can dual boot between the two.
However, I need some advice on how to do this.
I've tinkered with Ubuntu partitions in the past, but am very rusty and I don't want to damage my existing Ubuntu installation.

I know that my hard drive is approxiamtely 50% full and when I look in System Monitor, I can see that, but when I open GParted, it shows that my 'main' partition (for want of a better word), is full.
I want to resize the partition, to free up space, so that I can install Elementary OS, however, I'm concerned that I might delete or corrupt my data.

I have attached screen shots of both System Monitor and Gparted.

Can anyone advise what I need to do here?
I just want to do this in the easiest possible way, so if that means sharing my home directory/user name, I don't mind.
Thanks!


[ATTACH=CONFIG]259594[/ATTACH][ATTACH=CONFIG]259595[/ATTACH]

---

### Post by oldfred on 2015-01-29
You are using LVM, which supposedly makes it much easier to resize partitions, but you cannot use gparted but have to use LVM. And then would want to install into the LVM.

I do not know much about LVM. Some links with more info:
       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)
2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html)
[http://askubuntu.com/questions/470632/install-lvm-dual-boot-with-windows](http://askubuntu.com/questions/470632/install-lvm-dual-boot-with-windows)
Issues on very large 19TB LVM ext4 64 bit partition
[http://ubuntuforums.org/showthread.php?t=2213785](http://ubuntuforums.org/showthread.php?t=2213785)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay
LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm

---

### Post by alexeix on 2015-01-30
Thanks for all the resources.

I've taken a look, but this process does not seem straightforward; the LVM utility still shows my partition as completely full, which I don't understand.
I'm not confident about trying this without a full backup of my machine, so I may as well just install Elementary OS over Ubuntu (after I've made the backup!).

I'll come back to Ubuntu again, but I want to try Elementary.

---

### Post by yancek on 2015-01-30
> I'll come back to Ubuntu again, but I want to try Elementary. 		

The information you posted shows your partition is less than half full.  Install VirtualBox on Ubuntu and install Elementary in VirtualBox, then you'll have the opportunity to test Elementary and still have Ubuntu.

---

### Post by alexeix on 2015-01-30
Yes, that's right, I know my partition is less than half full, but the LVM utility doesn't see that.
I'm concerned that if I use it to re-size the partition, to free up space for a new partition, I may end up deleting/corrupting data.
I may try your suggestion of VirtualBox (thanks, as I hadn't considered it) for a test, but I think I'll need to do a full install of Elementary, in order to gauge any speed benefits.

---

