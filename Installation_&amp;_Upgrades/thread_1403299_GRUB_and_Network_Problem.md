---
title: "GRUB and Network Problem"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by vikrang on 2010-02-10
I have a C2D Dell VOSTRO 1500. I have XP as my primary OS.. I have a 160 GB HDD (SATA). 
 
Lately I have been attracted to Linux and want to migrate from MS Windows...
 
I have 3 partitions . 
1. NTFS for Win - 100 GB
2 - OpenSUSE 11.2 (GNOME) - 40 GB (ext4)
 
I have installed Ubuntu 9.10 in the balance 20GB I would like to do the following:
 
1. GRUB menu for Open SUSE 11.2 was more attractive with its green Splash screen. Ubuntu 9.1 is just like a DOS style plain Black and White menu. How do I include Ubuntu entry in the Open SUSE boot loader and delete the Ubuntu GRUB which over wrote the SUSE's boot menu?
 
2. I just want 3 entries in the Menu - XP,UBUNTU and OpenSUSE ...I dont want all the recovery and other misc options.In Open SUSE there is a convenient boot loader option in YAST which allows the user to modify.Using that i had removed similar entries in SUSE like (recovery, safe mode etc) I tried to edit Menu.lst by using gksudo gedit /boot/grub/menu.lst but I just got a blank file...I figured it must be like editing Autoexec.bat in Dos where if you dont enter correct path, editor will throw a blank screen which can still be saved...where is the file located? in etc or boot or Usr...Sadly I am not well versed with Linux commands and found it difficult to search..Is the file attrib 'hidden"?
 
3.I am sorry to combine different types of Queries but , 
 
(a) None of the network types work in Ubuntu,,,I have BCM4311 card which I know is a troublesome wireless option for Linux...9.10 is not at all detecting my network
Is there any automatic scanner which detects all the available networks?
 
(b) My High speed datacard (Mobile Broadband) is also not working in 9.10....It worked flawlesly in SUSE which had a similar interface like 9.10....
 
4. How do you uninstall a Linux distro safely and re-partition the drive (that is how do you tell GRUB to load the correct active OS and safely remove a partition. Also, is it possible to load only Windows in GRUB and later safely restore WIN natural NTLDR?
 
Thx...Sorry for the long mail

---

### Post by vikrang on 2010-02-14
THIS HAS BEEN SOLVED WRT SECOND PART ON NETWORKING

* I installed b43-fwcutter and wvdial and followed instructions in one of the threads which solved the problem..Downloading *broadcom-wl-4.80.53.0.tar.bz2 and apsta-3.130.20.0.o and running the below codes:p

sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o 
tar xfvj broadcom-wl-4.80.53.0.tar.bz2 
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o

---

### Post by darkod on 2010-02-14
To eliminate ubuntu recovery entries open:
sudo gedit /etc/default/grub

and add this line at the end or if it exists change the value:
**GRUB_DISABLE_LINUX_RECOVERY=true**

To eliminate memtest, execute:
sudo chmod -x /etc/grub.d/20_memtest86+

That makes the file unexecutable. To make it executable again use the same command with +x.

Run:
sudo update-grub

and new grub.cfg will be created with these changes. DO NOT try to edit or crete menu.lst for grub2, it doesn't use that file and if you create such file in /boot/grub you can confuse it.

If you have more questions, just ask but try to be specific, don't throw everything at once. :)
Also for the networking issues you might receive better help in the Networking subforum.

---

