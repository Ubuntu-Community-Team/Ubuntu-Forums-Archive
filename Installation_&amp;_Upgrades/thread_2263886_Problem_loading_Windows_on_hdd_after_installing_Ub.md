---
title: "Problem loading Windows on hdd after installing Ubuntu on USB flash"
date: 2015-02-04
forum: Installation &amp; Upgrades
---

### Post by akshay16 on 2015-02-04
First of all,  I'd like to apologize if this problem has already been solved. 
I am totally lost..! 
Please help me.

Config:
Hp laptop i5,4gb,1tb 
Windows 7 ultimate x64

I have tried installing the os on a USB flash drive from CD/DVD. 
And it successfully got installed through regular install.  
When plugged the pendrive in,  I can boot properly.  And While booting, I can select between Windows 7 and Ubuntu. 
But,  when I remove the pendrive, and turn the system on,   it shows some kind of GRUT LOADING...  error. 
And then,  I turn it off place the pendrive select the default boot drive,  and it successfully boots up. 
Please help me regarding this. 

And also would like to know the proper way of installing Ubuntu on a pendrive. 

Thank you.

---

### Post by yancek on 2015-02-04
The default for installing the Ubuntu Grub bootloader is to install to the master boot record of the first drive.  This is shown on the Installation Type window under 'Device for bootlaoder installation', /dev/sda.  If you left that default, the Grub boot code was installed to the mbr of your primary drive with windows.  This is a tiny portion of the boot code required to boot.  Almost all of the Grub boot code is on the partition on which you installed Ubuntu on the pendrive which is why it works with the pendrive attached and why it does not work without it.  If you had clicked the down arrow for 'Device for bootloader installation', you would have seen a number of options.  If you only had the 1TB drive and the pendrive attached, it most likely would have been '/dev/sdb'.

You can install the Ubuntu Grub bootloader to the master boot record of the flash drive.  You need to first ascertain whether it is sdb or something else.  Booting Ubuntu, opening a terminal and entering the command:  sudo fdisk -l(Lower Case Letter L in the command) will show you the drive/partition info to see if it is sdb.

In order to repair the windows bootloader, you probably need your windows installation medium, selecting the repair option.  I don't use windows so you could try an online search for other methods, how to repair windows bootloader' or something similar.

---

### Post by oldfred on 2015-02-04
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

 [https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

