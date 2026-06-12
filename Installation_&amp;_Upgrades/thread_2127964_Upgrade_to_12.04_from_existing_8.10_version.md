---
title: "Upgrade to 12.04 from existing 8.10 version"
date: 2013-03-21
forum: Installation &amp; Upgrades
---

### Post by backtothefuture on 2013-03-21
I currently have Ubuntu 8.10 along with win vista installed on my laptop.
I tried to upgrade to a newer version, but was not permitted as the 8.10 is no longer supported.
I have partition #5 setup for V8.10 at thjis time and have downloaded the 12.04 LTS iso file and burned to a cd.
I wish to install to the same partion as the existing V8.10.
Is there a way to do this and what steps are required.
Thanks for any help!

---

### Post by grahammechanical on 2013-03-21
First of all, have you tried Ubuntu 12.04 in a live session? Where there any problems? Assuming 12.04 runs fine in a live session on your machine, this is what you do:

1) Boot into the 12.04 DVD and let it run to a live session and when it gets to a desktop you click on Install 12.04
2) At the welcome screen select the language and select Install Ubuntu - see image (1) here

[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)

Another set of images

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

3) Follow the instructions for screens (2) and if necessary screen (3)
4) When you get to screen (4) Installation Type select "Do something Else"
5) This will bring you a the Gparted partitioner section. You will see something like this image

[http://gparted.sourceforge.net/screens/gparted_1_big.png](http://gparted.sourceforge.net/screens/gparted_1_big.png)

Select partition 5 - sda5 if that is where 8:10 resides - make sure of this
6) Click on "Change" and at the next screen select a file system - Ext4, a mount point of  /, click to format. You can resize the partition here also not it is not a requirement. When you click to continue you will get a message about it taking some time to resize the partiton. Ignore that message. We get that message even when we have not resized the partition. When you get back at the partitioning screen the changes that you made will show in the partitioner window. If you are happy with them, then click to install.

7) Follow instructions at images (6), (7), (8), (9) and (10) in the first link.

I am sorry that I cannot find a more up to date picture of the Do Something Else partitioning section.

May I give you a word of caution. When you choose to install third party software during the installation process, it will bring in a proprietary video driver. I have experienced problems (Ubuntu not getting to a desktop) when a proprietary video driver is installed. I test install images and I never install third party software at that stage. I always install it after installation. I always get to a working Ubuntu with the Open source driver. So, I recommend that you do not click to install third party software.

After installation you can search for Ubuntu Restricted Extras in the Ubuntu Software Centre. You can also install a proprietary video drivers from the Additional Drivers utility. It should pop up in the top panel soon after the desktop has loaded.

You will also benefit from reading through the Ubuntu Desktop Guide. There are big, big differences between 8:10 and 12.04. You will find it in the Dash under "help."  Or check it out here

[https://help.ubuntu.com/12.04/ubuntu-help/index.html](https://help.ubuntu.com/12.04/ubuntu-help/index.html)

Oh, another thing. 12.04 should reuse the existing swap partition. This link has an up to date image of the Allocate Drive Space section

[http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml](http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml)

Regards.

---

