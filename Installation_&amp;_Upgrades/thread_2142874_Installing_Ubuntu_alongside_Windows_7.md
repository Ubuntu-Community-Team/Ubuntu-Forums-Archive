---
title: "Installing Ubuntu alongside Windows 7"
date: 2013-05-07
forum: Installation &amp; Upgrades
---

### Post by rezaf on 2013-05-07
Hi, I know that this is duplicate question but I confused because of many references. 

my notebook have an HDD with 4 partitions (C,D,E,F). I installed windows 7 64 bit in the C partition (100GB space) completely and now want to install ubuntu 12.04.1 in the D partition that have 40GB space.
What is the best and risk-free method to do this ???

I know that can use methods to keep windows bootloader after installing ubuntu to choose between operating systems, or replace Grub bootloader (bootloader of linux) after installing ubuntu to choose between operating systems.
please learn to me both of them (keeping bootloader of windows and replacing linux bootloader) .

also I confuse in the installation steps of ubuntu 12.04.1. in the window that have this three selection : "install ubuntu alongside windows",  "replace windows with linux",  "some others",  which one is better for my purpose? 

when I choose "install ubuntu alongside windows", I go to the next page that have an slider to choose disk space, what does the slider do ?? (do this selection will copy ubuntu files to the windows partiotion 'C' and this slider means the space for everyone?? ) ?

in the partitioning tool that show my partitions, I choose the right partition for installing ubuntu(D or dev\sda5) and choose it again in the drop down list for installing linux bootloader in it (I prefer to use windows bootloader), is this true ? why the installer give error that don't find root info or loader in the selected drive (I'm not sure about the error message text but installer give this error when I select every drive) ???

also please say to me the ways for installing windows 7 after installing ubuntu.

I know that many new users of linux have this questions also I tried to completely ask my questions to find all answers and also may be this thread help to others and solve problems. I will be happy if you help me.

I suggest that support team of ubuntu make an video center and put step-by-step learning videos about this basic or advanced questions in it.

Very Thanks.
Regards.

---

### Post by fantab on 2013-05-07
Since you installed Windows, I presume you have Windows installation Disk. If this is indeed the case then I suggest you use GRUB Bootloader. Windows Boot Loader will not boot Linux. You have to use a utility called [EasyBCD]("https://neosmart.net/EasyBCD/"). Which in other words, it makes you dual boot Linux from Windows.
If you want to use EasyBCD then you have to install GRUB in the same partition you Ubuntu installed.


You want Ubuntu to install on your 40GB D: partition. (Rememer in Linux your partition numbers are labled differently. Your First HDD will be /dev/sda and its First partition will be /dev/sda1 (C)  , your second partition will be /dev/sda2 (D) and so on. If you have a second HDD then that will be /dev/sdb and so on). During Ubuntu Install when you are asked to select "Installation Type" choose "Something Else". This will lead you next dialog which will list all your partitions. Select the partition on which you want to install Ubuntu and hit "Change" a new dialog will open. Choose to format this partition with filesystem, ext4 and use "/" as mountpoint. Done. Then Install. Grub will be used.

---

### Post by oldfred on 2013-05-07
Some say EasyBCD works, but it uses grub4dos to chain load to the grub install in the Linux partition. But grub2 does not correctly install to a partition. It can be forced, but on updates you may have to reinstall grub as it uses blocklists or hard coded addresses to find the rest of grub & menu. If an update moves a file on the drive the the address is wrong and you have to reinstall grub.

If partitions already exist of a size you want then you can use manual install. Click change and that also lets you create partitions or use existing, but it lets you choose which partition is mounted as / and its format ext4. You also then can select /home ext4 and swap. If reinstalling you mount /home but DO NOT format it so it keeps your existing data.

 Install options, Do not use erase entire drive unless that is really what you want.
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

