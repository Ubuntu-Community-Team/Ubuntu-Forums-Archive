---
title: "Disk partitions and UEFI"
date: 2015-11-24
forum: Installation &amp; Upgrades
---

### Post by virdfel on 2015-11-24
hi there,
happy to be a part of Ubuntu community, hope I will : ]
but before, I need some help with install
*have already windows 7 on drive

1. start was not so colorful:
[[IMG]http://storage5.static.itmages.ru/i/15/1124/s_1448357841_1370579_5e6ee21e4f.jpg[/IMG]]("http://itmages.ru/image/view/3234199/5e6ee21e")

2. bios:
[[IMG]http://storage6.static.itmages.ru/i/15/1124/s_1448357841_1583442_a6a97bf0e9.jpg[/IMG]]("http://itmages.ru/image/view/3234200/a6a97bf0")

3. tried setup and had the message:
[[IMG]http://storage4.static.itmages.ru/i/15/1124/s_1448357840_7560495_8dceb854c3.jpg[/IMG]]("http://itmages.ru/image/view/3234198/8dceb854")
> This machine's firmware has started the install in UEFI mode but if look like there may be existing operating systems already installed using "BIOS compatibility mode". If you continue install Debian in UEFI mode, it might be difficult to reboot the machine into any BIOS-mode.
If you wish to install in UEFI mode and don't care about keeping the ability to boot one of the existing systems, you have the option to force that here, if you with to keep the option to boot an existing operation system, you should choose NOT to force UEFI installation here.

4. loaded livecd, opened GParted, and... on unallocated space can create only "Primary partition"
[[IMG]http://storage3.static.itmages.ru/i/15/1124/s_1448357840_6258702_12ede7b7cb.png[/IMG]]("http://itmages.ru/image/view/3234197/12ede7b7")

so... what I must do?
1) create correct partitions

sd1 - system C win
sd2 - extended
 -- sd5 - logical, D in win
sd6 - extended
 -- sd7 - logical, root
 -- sd8 - logical, swap
 -- sd9 - logical, home

OR

sd1 - system C win
sd2 - extended
 -- sd5 - logical, D in win
 -- sd6 - logical, root
 -- sd7 - logical, swap
 -- sd8 - logical, home

2) what to do with UEFI? how to install correct and have choise beetween windows and ubuntu before load?

thanks,

---

### Post by TheFu on 2015-11-24
a) please post text or links. Images aren't nice for people without broadband connections.
b) Please run "boot-repair" and post the information link it creates. This will provide most of the data we need to provide advice. Run this off the live-boot-CD or flash drive.  "Try Ubuntu" ... 
c) BIOS vs UEFI. If each OS installed on the system don't use the same boot method, it is a hassle to boot either. 99.9999% of people decide to have 100% BIOS for their OSes on a machine or 100% UEFI. Mixing is just too much hassle. Plus if changed, then Windows would need to be reinstalled.  So .... whatever boot method is used by the current OS on the system is what you want to use for Linux.

Some lite reading on UEFI: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by yancek on 2015-11-24
The message you posted indicates you are booting Ubuntu in UEFI mode and that your windows 7 installation uses MBR BIOS.  They are incompatible and if you were to proceed either or both would be unbootable.  I don't use UEFI myself but from what I understand, when you boot Ubuntu there should be an option to boot UEFI or MBR/BIOS.  You need to select MBR/BIOS to install.

>  	 4. loaded livecd, opened GParted, and... on unallocated space can create only "Primary partition"

Yes, that's correct because your Extended partition is entirely taken up by the windows partition so you have the option of using the 50GB unallocated space as / (root filesystem) and a small swap.  The other option is to shrink the second large windows partition from windows Disk Management to give you space in which to create another logical partition for / or /home.  I think you need another drive because your current one is almost full.

---

### Post by grahammechanical on 2015-11-24
Your Windows 7 is installed in BIOS or legacy mode, which is normal for Windows 7 but your motherboard has a UEFI boot system and you are loading Ubuntu in EFI mode. So, load Ubuntu in legacy mode because both Windows and Ubuntu need to be installed in the same Mode. 

As for your partitions.

With MBR partitioning we are allowed a maximum of 4 primary partitions and 2 are already used up - sda1 is a primary partition and sda2 is a special primary partition called an Extended partition. We can create many Logical partitions inside an extended partition to overcome the 4 primary partition limit. You already have one logical partition (sda5) inside sda2.

You can expand sda 2 (extended partition) into that 50.72 GiB unallocated space and then create the 3 logical partitions inside the extended partition (sda2) that you can use for Ubuntu.

So, 

1) resize sda2 so that the unallocated space is inside sda2
2) do not resize sda5
3) create the three logical partitions out of the unallocated space inside sda2 to be used for Ubuntu.

Regards

---

### Post by virdfel on 2015-11-24
thanks!
finally in :smile:
[[IMG]http://storage8.static.itmages.ru/i/15/1124/s_1448388056_6326164_ec11dc98b9.png[/IMG]]("http://itmages.ru/image/view/3236362/ec11dc98")

---

