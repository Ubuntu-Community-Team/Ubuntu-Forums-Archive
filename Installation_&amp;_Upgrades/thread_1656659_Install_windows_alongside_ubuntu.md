---
title: "Install windows alongside ubuntu"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by Dyffo on 2010-12-31
I have Ubuntu installed , VERY occasionally I need access to Windows. Is there a simple way for me to do this. I want first boot into UBUNTU with an option to go into Windows. I have a Windows install cd.

---

### Post by howefield on 2010-12-31
Have a look at VirtualBox, an application which will allow you to install  Windows as a virtual machine which can be run simultaneously with your Ubuntu OS.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

Short videos about VirtualBox here

[http://www.virtualbox.org/wiki/VirtualBoxTV](http://www.virtualbox.org/wiki/VirtualBoxTV)

---

### Post by Dyffo on 2010-12-31
> **howefield said:**
> Have a look at VirtualBox, an application which will allow you to install  Windows as a virtual machine which can be run simultaneously with your Ubuntu OS.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

Short videos about VirtualBox here

[http://www.virtualbox.org/wiki/VirtualBoxTV](http://www.virtualbox.org/wiki/VirtualBoxTV)

Yes I have had virtual Box - but it is far too slow - and a lot of the stuff I need to download and work on will not run in V.B.Thanks for your suggestion.

---

### Post by Rubi1200 on 2010-12-31
Hi,
please post the output of the following command:
```
sudo parted -l
```
This will give us a quick overview of your drive setup and make advising you easier.

Thanks.

---

### Post by Dyffo on 2010-12-31
> **Rubi1200 said:**
> Hi,
please post the output of the following command:
```
sudo parted -l
```
This will give us a quick overview of your drive setup and make advising you easier.

Thanks.

mike@mike-desktop:~$ sudo parted -l
[sudo] password for mike: 
Model: ATA SAMSUNG SP2504C (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  247GB  247GB   primary   ext3            boot
 2      247GB   250GB  3076MB  extended
 5      247GB   250GB  3076MB  logical   linux-swap(v1)
Here it is -

---

### Post by presence1960 on 2010-12-31
> **Rubi1200 said:**
> Hi,
please post the output of the following command:
```
sudo parted -l
```
This will give us a quick overview of your drive setup and make advising you easier.

Thanks.

+1 

Very important prior to proceeding.

You can shrink your Ubuntu partition to allocate the space you want to give windows. You must do so using gparted from the Ubuntu Live CD/USB, as you can not shrink the Ubuntu partition from Ubuntu since it will be mounted.

You then have 2 choices. You can leave the space as unallocated and boot the windows install CD/DVD and install to the unallocated space, or while still in gparted you can create a **_primary NTFS partition_** and install to that when you boot the windows CD/DVD.

After the install make sure windows boots fine & is working properly. 

You will now have to reinstall GRUB to the MBR. Boot the ubuntu Live CD/USB and choose to "try ubuntu without any changes," When the desktop loads open a terminal and run ```
sudo mount /dev/sda1 /mnt
```This will mount your ubuntu / partition.

Next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sda
``` This will put GRUB back in the MBR. Reboot without Ubuntu Live CD/USB and you should be good to go.

---

### Post by presence1960 on 2010-12-31
> **howefield said:**
> Have a look at VirtualBox, an application which will allow you to install  Windows as a virtual machine which can be run simultaneously with your Ubuntu OS.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

Short videos about VirtualBox here

[http://www.virtualbox.org/wiki/VirtualBoxTV](http://www.virtualbox.org/wiki/VirtualBoxTV)

Virtual Box is a viable option, **_*if*_** you have enough RAM in your machine for it to run effectively.

---

### Post by Dyffo on 2010-12-31
> **presence1960 said:**
> Virtual Box is a viable option, **_*if*_** you have enough RAM in your machine for it to run effectively.

             total       used       free     shared    buffers     cached
Mem:           993        913         80          0         93        489
-/+ buffers/cache:        329        663
Swap:         2933          0       2933

This is what I have

---

### Post by presence1960 on 2010-12-31
> **Dyffo said:**
> total       used       free     shared    buffers     cached
Mem:           993        913         80          0         93        489
-/+ buffers/cache:        329        663
Swap:         2933          0       2933

This is what I have

If I am interpreting that info correctly, you have 1 GB of RAM installed. Remember that you run virtual box from the host OS (Ubuntu). Even though Ubuntu uses RAM differently and more efficiently than does Windows, I would say you do not have enough RAM to split between Ubuntu and Virtual Box to have it run nicely. Even if you gave windows half of your RAM that is not much. You might be better dual booting, but that depends on what you want to do on windows and how patient you can be with Virtual Box on about 1/2 GB of RAM.

---

### Post by presence1960 on 2010-12-31
I run windows in Virtual Box, which was basically set up as a test to learn Virtual Box. But I was able to give it 1.8 GB of RAM because I have 4 GB RAM in my machine. It runs nicely with 1.8 GB of RAM. Even though this was a test setup, I have never gotten rid of it. I still have a true multi-boot setup with Ubuntu 10.10, Windows 7 & Sabayon. My windows in Virtual Box is XP Professional.

---

### Post by Dyffo on 2011-01-01
> **presence1960 said:**
> +1 

Very important prior to proceeding.

You can shrink your Ubuntu partition to allocate the space you want to give windows. You must do so using gparted from the Ubuntu Live CD/USB, as you can not shrink the Ubuntu partition from Ubuntu since it will be mounted.

You then have 2 choices. You can leave the space as unallocated and boot the windows install CD/DVD and install to the unallocated space, or while still in gparted you can create a **_primary NTFS partition_** and install to that when you boot the windows CD/DVD.

After the install make sure windows boots fine & is working properly. 

You will now have to reinstall GRUB to the MBR. Boot the ubuntu Live CD/USB and choose to "try ubuntu without any changes," When the desktop loads open a terminal and run ```
sudo mount /dev/sda1 /mnt
```This will mount your ubuntu / partition.

Next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sda
``` This will put GRUB back in the MBR. Reboot without Ubuntu Live CD/USB and you should be good to go.
All done, I boot up am offered my Ubuntu and or Windows, however this morning I find that windows will not connect to the internet. I am connected by cable thro' the Ethernet port.Do you think a reinstall / repair of Windows would solve the problem. All is well with Ubuntu so the card/motherboard must be O.K.

---

### Post by Dyffo on 2011-01-01
Solved reinstalled Drivers - used a USB Modem Stick to get connected.

---

