---
title: "What possibilies for dual boot  W7 / Ubuntu?"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by Len666 on 2010-12-18
Hi,
 
I have a HP G62-144DX laptop with Core3 processor, 500 gB HD, Windows 7 Home Premium.
 
I want to install Ubuntu 10.4 cause with 10.10 (as single OS) I have had some issues with the wifi adapter, my only connection with the internet. I reformatted completely and installed W7 again so I have my internet connection back. 
 
I have asked several sources, also in the beginners talk section how to install ubuntu so I get a dual boot option. The problem is I get so many different answers pointing at different risks and problems. Also there are different ways, within W7 or not, of which I don't know the (dis-)advantages.
 
Is there someone who is experienced in this field and willing to help me step by step?
 
So, I have made a new partition on my HD, 100 gB. I have Ubuntu 10.4 Lucid Lynx. I made a backup of my present system.
 
Questions: What possibilities do I have for creating a choice at boot-up: W7 or Ubuntu What are the (dis-) advantages
Which choice is best for a well performing and reliable PC? 
 
 
Thanks for your time.
Len.

---

### Post by sikander3786 on 2010-12-18
Hi.

So you want to know about different scenarios of installation like a proper dual boot and Wubi?

And you want to know about bootloader i.e, Grub vs Windows based bootloader for dual-boot?

The best possibility is to install Ubuntu in a proper dual boot to Windows and let Grub do the dual-boot job for you.

Have a go at this page.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

We can guide you but we need to know exactly what you want to achieve ;-)

---

### Post by Pillars of Creation on 2010-12-18
If you just want to dual-boot Windows 7 and one flavor of Ubuntu that&#8217;s easy. Basically you want to install Windows 7 first at the front of the drive in a primary partition. Then install Ubuntu in a partition after the Windows 7 partition or partitions. Grub2 will automatically setup a boot menu where you will have the option of booting Windows 7 or Ubuntu.

When you boot to Windows 7 install disk you want to select CUSTOM ADVANCED, NEW, HARD DRIVE SPACE = 

Then select the space you want to give Windows 7 in megabytes. So if you want to give it a 50 gigabyte partition select 50,000. If Windows 7 wants to make any additional partitions go ahead and let. 

When you get done with the Windows install put in your Ubuntu disk. Then load Ubuntu from the CD in a live session and start the GParted utility. Make a partition for Ubuntu. Then reboot and install Ubuntu into the partition you made for it.

Grub2 will automatically give you a good option for the two OS&#8217;s.

The reason you want to install the operating systems in the order of Windows first and Ubuntu second is that Windows will destroy whatever came before it. Also Windows 7 has to be installed in a primary partition and it is best to have primary partitions at the front of the drive. Ubuntu plays well with Windows 7.

Note that some people will say Ubuntu must be installed in a primary partition. This is not true. It doesn&#8217;t really matter whether Ubuntu is installed into a primary or a logical partition. However on a given system you can only have four primary partitions or three primary partitions and an extended partition.

In a system with three primary partitions in an extended partition you can have multiple logical partitions within the extended partition.

---

### Post by Len666 on 2010-12-19
You guys rock. I have spent quite some time behind my pc but this knowledge re. drives and partitions just  doesn't come automatically.

---

