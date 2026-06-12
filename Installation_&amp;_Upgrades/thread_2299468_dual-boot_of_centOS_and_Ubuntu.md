---
title: "dual-boot of centOS and Ubuntu"
date: 2015-10-18
forum: Installation &amp; Upgrades
---

### Post by newcfd on 2015-10-18
I installed centOS in my computer before and now want to add Ubuntu to it.
When I used GParted to check the partition table, there is only one
partition for CentOS(not three, swap, root and home) with a key sign 
for it which means it is in use. May I still go ahead to shrink this partition
to make rooms for Ubuntu? Any dangers?  Thanks for you help

---

### Post by james_moore2 on 2015-10-18
You should be able to use the installer and there should be an option called "Install along with centOS" or something like that if there isnt please provide pictures and I will try to help you from there.

---

### Post by newcfd on 2015-10-18
No option for  "Install along with centOS". I did not see it in the installation process. Please see the attached the partition file.


> **james_moore2 said:**
> You should be able to use the installer and there should be an option called "Install along with centOS" or something like that if there isnt please provide pictures and I will try to help you from there.

---

### Post by newcfd on 2015-10-18
found this link[URL="http://ubuntuforums.org/showthread.php?t=2054664"]
http://ubuntuforums.org/showthread.php?t=2054664[/URL]

[COLOR=#000000]"You cannot use gparted on LVM and have to use some other tools also."
[/COLOR][FONT=-apple-system]GParted doesn&#8217;t have support for LVM disks.

[/FONT][COLOR=#111111][FONT=Ubuntu]the latest version of Gparted (0.14) supports resizing LVM physical volumes. The one I use is 0.18. It may work. [/FONT][/COLOR]

---

### Post by yancek on 2015-10-18
You have CentOS installed using LVM and as you can see in the image you posted, it uses the entire drive.  You will have to resize (shrink) that partition to make room on which to install Ubuntu.  You can't do it the way you resize standard partitions.  The links oldfred posted should have some info, otherwise just do an online search for resize lvm.

---

### Post by newcfd on 2015-10-18
deactivated the partition /dev/sda2 and tried to use GParted to reduce its size. It does not work. I can set a size for free space. But after I pressed return, it went back to zero.
checked GParted home and found it supports lvm2 pv. Why does not it work?

---

### Post by newcfd on 2015-10-18
I managed to reduce the size of LVM partition. But I can not see the unused partition I just reduced from the LVM partition in the installation(Installation type: something else).

---

### Post by oldfred on 2015-10-18
I still do not know LVM, but how you resize LVM is different than standard partitions with gparted.
The newer versions of Ubuntu include LVM as part of desktop installer, so installer should see the LVM.

Some links that may be helpful. 
 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)
2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html)
[http://askubuntu.com/questions/470632/install-lvm-dual-boot-with-windows](http://askubuntu.com/questions/470632/install-lvm-dual-boot-with-windows)

---

