---
title: "Installing Ubuntu on a secondary hard drive with data already stored"
date: 2013-10-03
forum: Installation &amp; Upgrades
---

### Post by BIlly_Yu on 2013-10-03
Hi Ubuntu community! Totally new to Ubuntu and wanted to try a Linux-based system since I am getting into programming code in Linux. I was wondering how I would go about installing Ubuntu on my secondary hard drive. Here's my setup:
[INDENT]
I have 2 drives. 250GB SSD and a 500GB HDD. I currently have Windows 8 installed onto my SSD so I will be unplugging that during the Ubuntu installation. Now my 500GB HDD currently has programs installed from windows.
I've tried installing Ubuntu on my 500GB HDD but I can't seem to find the right option for me. When it asked me where I want to install Ubuntu I went to "Something else" and it took me to the partition screen. It gave me an option to create a new partition table but it told me that it would erase everything I had on there? 

Next I tried to select "Change" option that allowed me to choose the size of the drive and select it's purpose (ie. Do not use as a partition). I'm pretty much stumped here as to what to do...
[/INDENT]

So how would I go about installing Ubuntu without messing with my installed programs from Windows? Do I need to change my partition size in Windows Disk Management to create free space for Ubuntu?
Thanks again. Hopefully, there is an easy solution to this? haha

P.S. I've tried searching about this topic, but none of the threads really were specific to my case.

---

### Post by michiel-reenaers on 2013-10-03
Go into try Ubuntu when you boot the live install cd/usb. 

WHat you do then is: 
open a terminal (left upper corner dash - type term - press terminal)
Type: sudo apt-get install gparted
it is possible that you have install problems while trying to install gparted check google if that's the case. 

open gparted: type in terminal sudo gparted or go to dash and search gpart. 
Here you can change your partitions
Be aware!!!! this is very dangerous it's always recomended to make a backup before changing anything
now select your hdd
right mouse button (or in the menu above) select resize partition
make the partition at least 10 gb shorter (at least 20 is recomended if you whish to use it frequently)
now you should have free memory that is unallocated (it's also described as unallocated) 
right-click it and make it ext4
now make your changes definitive (upper menu).

wait untill it says everything has been changed
close gparted
press on the desktop install ubuntu
now select something else
select the newly made partition
now you should be good and the installation should finish on it's own. 
(it's also recomended you make an additional partition of around 1mb free for your swap) .
To ensure you do not lose any important data of ubuntu should something go wrong in the future you can make two seperate partition one for your root and one for your home.

You can always PM me or ask if you want a more detailed step-by-step explanation

---

### Post by mastablasta on 2013-10-03
check about UEFI install if you are running windows 8 in uefi mode.: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

anyway the easiest way to do it is to defragment the drive and then rezise the partition. this should give you an emtpy space (unformatted) where ubuntu will be installed. then during installrpocess you can just tell it to install to largest empty disk space. all is formatted automaticly.

you might need to update grub for dual boto to work propperly. thi scan be done using the boot repair tool: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

i suggest you allocate about 20-25 GB disk space or more (though it can run on 8 GB think).

another option to give it a go is to use virtualbox: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by oldfred on 2013-10-03
The installer or gparted may not show existing Windows NTFS partition for several reasons all need to be resolved before proceeding.

NTFS partition need chkdsk. Sometimes Windows will still work but partition needs chkdsk. 
You converted drive from basic partitions (MBR or msdos) to dynamic.
You had drive partitioned with gpt and Windows converted to MBR. But Windows does not fully convert and leaves backup gpt partition table. You can remove backup.
Drive is configured with RAID.
       Most of reasons for installer not showing Windows, any partition type error
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

Post this as a start from terminal in live installer.
sudo parted -l
sudo fdisk -lu

---

### Post by BIlly_Yu on 2013-10-03
> **michiel-reenaers said:**
> Go into try Ubuntu when you boot the live install cd/usb. 

WHat you do then is: 
open a terminal (left upper corner dash - type term - press terminal)
Type: sudo apt-get install gparted
it is possible that you have install problems while trying to install gparted check google if that's the case. 

open gparted: type in terminal sudo gparted or go to dash and search gpart. 
Here you can change your partitions
Be aware!!!! this is very dangerous it's always recomended to make a backup before changing anything
now select your hdd
right mouse button (or in the menu above) select resize partition
make the partition at least 10 gb shorter (at least 20 is recomended if you whish to use it frequently)
now you should have free memory that is unallocated (it's also described as unallocated) 
right-click it and make it ext4
now make your changes definitive (upper menu).

wait untill it says everything has been changed
close gparted
press on the desktop install ubuntu
now select something else
select the newly made partition
now you should be good and the installation should finish on it's own. 
(it's also recomended you make an additional partition of around 1mb free for your swap) .
To ensure you do not lose any important data of ubuntu should something go wrong in the future you can make two seperate partition one for your root and one for your home.

You can always PM me or ask if you want a more detailed step-by-step explanation

Hmm. This seems more complicated than I thought. I'll give this a try when I have time since I am working.

---

